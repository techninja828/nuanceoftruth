Mission
Create a trusted debate platform that surfaces well-sourced claims, highlights their impact, and converges on informed consensus through structured dialogue and accountable participation.

Primary Users & Roles
Creators: Draft claims, counter-arguments, and supporting context with required citations.
Validators: Review submissions for citation integrity, duplication, neutrality, and administer comprehension quizzes gating voting.
Moderators: Enforce civility policies, resolve disputes, and escalate appeals.
Observers/Voters: Consume debate trees, pass quizzes, cast impact votes, and join consensus polls.

MVP Scope
Debate Structure: Topics with root prompt, branching Pro/Con claims, citation attachment/validation.
Identity Layer: Backend KYC through W3C VC/DID broker, app-facing aliases, ZK uniqueness for votes.
Interaction: Impact voting post-quiz, consensus poll participation, validator task queues, moderator dashboard.
Data Access: Public read API (topics/claims), daily export snapshot, Snowflake licensing pipeline.
AI Assist: Citation suggestions and summarization support (human-in-loop).
Non-Goals (MVP)
On-chain governance or token issuance.
Native mobile apps.
Monetized licensing contracts (pilot only).
Automated moderation decisions without human review.

Success Metrics
≥95% published claims with validated citations.
≥80% quiz completion-to-vote conversion within 24h.
Median validator turnaround <4h per submission.
≥70% of active voters pass comprehension quizzes on first attempt.
Daily export delivery reliability ≥99%.

Release Assumptions
KYC vendor supplies revocable VCs and DID resolution SLA <1s.
Semaphore-like ZK uniqueness library ready for backend integration.
Neo4j Aura or managed cluster provisioned.

Validators recruited and trained pre-launch.

Legal review complete for data licensing terms.
