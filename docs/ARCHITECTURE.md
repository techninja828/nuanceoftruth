# Architecture Overview
The Reels-style evolution of Nuance of Truth introduces reaction-driven branching and balanced exposure heuristics. The platform remains service-oriented but now emphasizes real-time lesson routing, explainable recommendations, and rapid content iteration.

## Logical Layers
1. **Client Applications** – React Native/Next.js experiences that stream vertical video, collect reactions, surface context overlays, and render "why you saw this" explanations.
2. **API Gateway** – Authenticates session tokens, rate-limits reactions, and fans out to specialized services via REST/gRPC.
3. **Experience Services** – Microservices that orchestrate feed assembly, reaction routing, and follow-up selection.
4. **Content Intelligence** – Graph + analytics layer that maintains lesson metadata, perspective pairings, bias scores, and performance telemetry.
5. **Operational Fabric** – Monitoring, logging, feature flagging, and experimentation scaffolding for rapid tuning of exposure balance.

## Core Services
- **Feed Orchestrator** – Builds personalized lesson queues by combining viewer state, topic preferences, and required balance constraints.
- **Reaction Router** – Writes reaction events, runs the pairing heuristic (e.g., agreement → counterpoint, disagreement → reinforcement), and returns the next asset ID with rationale metadata.
- **Lesson CMS** – Handles media storage, caption/transcript generation, citation attachments, and reaction-branch configuration.
- **Validation Queue Service** – Coordinates fact-check tasks, bias tagging, and approval workflows before lessons reach production feeds.
- **Explanation Service** – Generates the short textual justification that accompanies each follow-up clip (“You disagreed, so here’s a fundamentals refresher to check assumptions”).

## Data Stores
- **Graph Store (Neo4j or similar)** – Models lessons, sources, reactions, and pairing edges with attributes for polarity, tone, and validation status.
- **Object Storage + CDN** – Houses video assets, captions, and thumbnails optimized for rapid mobile delivery.
- **Event Stream (Kafka/PubSub)** – Captures reaction events and watch telemetry for analytics, experimentation, and real-time guardrails.
- **Analytics Warehouse (Snowflake/BigQuery)** – Aggregates exposure balance, sentiment signals, and conversion metrics for dashboards and governance reviews.

## Key Flows
1. **Lesson Publication**
   - Curator authors a lesson in the CMS, attaching sources and proposed reaction branches.
   - Validation guild reviews citations and branch logic; upon approval the lesson node and pairing edges are activated in the graph.
   - Feed orchestrator ingests the updated graph snapshot to refresh eligible queues.
2. **Viewer Session**
   - Client requests initial queue from Feed Orchestrator, which applies balance requirements (e.g., ensure contrasting viewpoint within next 3 lessons after an agreement).
   - Viewer watches, selects a reaction; Reaction Router records the event, checks guardrails (fatigue, overexposure), and responds with next lesson + explanation string.
   - Event stream forwards reaction and watch data to analytics; explanation service logs the decision trail for auditability.
3. **Governance & Monitoring**
   - Stewards review dashboards fed by the analytics warehouse to monitor exposure balance, watch-through, and frustration indicators.
   - Automated alerts trigger when reaction mix skews (e.g., too many counterpoints without reinforcement) or when lessons receive repeated “Learn More” without adequate follow-ups.

## Safety & Privacy Considerations
- Pseudonymous identity tokens track session history without storing PII in the content graph.
- Reaction routing decisions are logged with hashes so auditors can reconstruct why any clip was shown.
- Source citations and bias metadata remain first-class fields, allowing viewers to inspect provenance within the UI.

## Extensibility Notes
- Feature flags enable A/B testing of new reaction types or explanation phrasing without redeploying core services.
- The pairing heuristic can evolve from rule-based logic to a supervised model while retaining human-approved guardrails from the Validation Guild.
