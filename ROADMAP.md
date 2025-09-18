# North Social Development Roadmap

This document outlines the planned phases for the development of the North Social protocol and its reference implementations.

### Phase 0: Specification & Community Building (Current)

*   **Objective:** Formalize the core protocol and build a founding team.
*   **Key Results:**
    *   [x] Create public GitHub repository with core documentation.
    *   [ ] Refine and finalize V1 of the technical specification based on community feedback.
    *   [ ] Recruit a core team of 2-4 developers to begin work on the reference implementation.
    *   [ ] Establish official communication channels (e.g., Matrix).

### Phase 1: CLI Reference Implementation (Proof-of-Concept)

*   **Objective:** Validate the most fundamental aspects of the protocol.
*   **Key Results:**
    *   [ ] Develop a command-line application in a systems language (e.g., Rust, Go).
    *   [ ] Implement DID and keypair generation.
    *   [ ] Implement local PDR creation and signed commits (e.g., a simple text post).
    *   [ ] Implement basic peer-to-peer connectivity and data synchronization between two CLI nodes.

### Phase 2: Core Home Node (HN) Implementation

*   **Objective:** Build a robust, standalone Home Node server.
*   **Key Results:**
    *   [ ] Implement the full RAIR sharding, distribution, and retrieval system.
    *   [ ] Integrate the DHT and PubSub messaging layers.
    *   [ ] Implement the proactive timeline materialization service.
    *   [ ] Develop a secure pairing mechanism for a CA to connect to the HN.
    *   [ ] Package the HN for deployment on common single-board computers (e.g., as a Docker container).

### Phase 3: Client Application (CA) and UI

*   **Objective:** Create a user-friendly client for interacting with the network.
*   **Key Results:**
    *   [ ] Develop a cross-platform (mobile/desktop) reference Client Application.
    *   [ ] Implement the secure communication channel to the HN.
    *   [ ] Build the core UI for timeline viewing, posting, and user interaction.
    *   [ ] Implement optimistic UI updates for a responsive user experience.
    *   [ ] Implement client-side logic for managing moderation list subscriptions.

### Phase 4: Network Scaling & Optimization

*   **Objective:** Enhance the protocol and software for wide-scale adoption.
*   **Key Results:**
    *   [ ] Implement and test the decentralized search indexer specification.
    *   [ ] Develop resource management systems for HNs (e.g., storage/bandwidth quotas).
    *   [ ] Conduct performance and security audits of the reference implementations.
    *   [ ] Develop user-friendly onboarding tools, including pre-configured HN images.
