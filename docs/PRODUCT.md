# Product Vision
Nuance of Truth is a responsive learning feed that borrows the effortless pace of "Reels" but replaces passive scrolling with purposeful reflection. Every clip is a micro-lesson anchored in cited facts. After watching, the viewer picks a reaction—**Agree**, **Disagree**, **Neutral**, or **Learn More**—that becomes the routing logic for what they see next. Agreement gently nudges toward credible counterpoints, disagreement reinforces foundations before expanding to new angles, and curiosity opens optional deep dives. The goal is to widen perspective without overwhelming or shaming the participant.

## Primary Users & Roles
- **Viewers** – Consume micro-lessons, provide structured reactions, bookmark threads, and request deeper dives.
- **Lesson Curators** – Assemble short-form lessons with sources, pairings, and reaction pathways; maintain tone and accessibility.
- **Perspective Editors** – Design the contrasting content journey, ensuring that each reaction offers intellectually honest exposure to adjacent or opposing ideas.
- **Validation Guild** – Fact-check sources, tag bias indicators, and approve reaction pairings to guarantee credible counterpoints.
- **Community Stewards** – Monitor sentiment health, manage escalation queues, and facilitate iterative improvements to the recommendation heuristics.

## Core Experience Pillars
1. **Reaction-Guided Flow** – Reactions replace endless swipe-up. Each choice triggers a new branch: e.g., selecting *Agree* reveals a respectfully framed challenge, while *Learn More* opens a stack of explainer reels and reading links.
2. **Balanced Exposure Engine** – Behind the feed lives a pairing matrix that scores content for topical diversity, evidentiary strength, tone, and novelty. High agreement streaks trigger balancing clips; sustained disagreement introduces empathy-driven explainers before opposing claims.
3. **Micro-Lesson Composition** – Lessons are capped at ~60 seconds, include on-screen source callouts, and surface interactive annotations for deeper context without pausing momentum.
4. **Participation Without Punishment** – Feedback always leads somewhere constructive. The UI highlights why a particular follow-up appears (“You agreed, here’s a credible counterpoint to consider”) to maintain agency and trust.

## MVP Scope
- **Reels Feed & Player** – Vertical video feed with lightweight overlays (title, source badge, reaction buttons, progress meter).
- **Reaction Router** – Client-side capture of reactions, server-side routing service that maps reaction + history to next lesson or branch.
- **Lesson Authoring Workspace** – Tools for curators to upload media, add captioning, cite sources, and define the reaction matrix for each lesson.
- **Validation Workflow** – Guild queue for reviewing citations, ensuring reaction pathways provide balance, and approving publish-ready lessons.
- **Telemetry & Sentiment Dashboard** – Monitor reaction mix, watch-through rates, and exposure balance scores in near real time.

## Deferred for Post-MVP
- Adaptive voiceover translation and accessibility localization.
- Advanced personalization based on psychographic profiles.
- Tokenized incentives or DAO-managed governance.
- Automated moderation without human review.

## Success Signals
- ≥70% of lessons include at least one follow-up viewed after the initial reaction.
- Balanced exposure score (share of contrasting viewpoints delivered following agreement) ≥0.6.
- ≥85% citation approval rate on first submission from curators.
- Drop-off after disagreement selections <15% within a session.
- ≥50% of “Learn More” selections convert into deeper content engagements (articles, long-form videos, or discussion rooms).

## Key Assumptions
- Reliable supply of high-quality, rights-cleared short-form content.
- Reaction pathways can be authored and validated within a 24-hour SLA.
- Viewer identity system can track session history while honoring privacy requirements.
- Sentiment analytics tooling is available to detect frustration or fatigue signals early.
