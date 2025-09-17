Diagram Overview
Logical layers: Web App ↔ API Gateway ↔ Application Services → Neo4j Graph & Snowflake Exporter; AI Services & Auth Broker integrated laterally; Monitoring wrapping all components.

Components
Web App: React/Next front-end, handles debate tree navigation, quiz gating, moderator/validator consoles.
API Layer: RESTful services enforcing role checks, ZK proof verification, citation validation orchestration.
Neo4j Graph: Primary debate store (Topics, Claims, Sources, Users), relation-driven queries.
AI Services: Managed LLM endpoints for citation suggestions, summaries (human oversight).
Auth Broker: VC/DID verification service interfacing with KYC provider; issues alias + ZK identity credentials.
Snowflake Pipeline: ETL jobs exporting sanitized debate data for licensing/API.
Monitoring & Logs: Centralized logging, metrics, audit trails.

Data Segregation
VC hashes & status stored in dedicated identity microservice (encrypted).
Application DB (Neo4j) holds alias IDs only; no PII.
Snowflake exports exclude identity references beyond alias ID and proof tokens.
Audit logs separated (immutably stored) with access controls.

Key Flows
Post Claim: Creator authenticates via alias, submits claim + citations; API triggers validator task; on approval, claim node created in Neo4j with PRO/CON relation.
Vote with ZK Proof: User passes comprehension quiz; Semaphore-like proof generated client-side, API verifies uniqueness, records VOTED relation with impact score.
Daily Export: Scheduler extracts Neo4j data, transforms to tabular schemas, pushes to Snowflake and Parquet bundles, publishes export manifest to API.
