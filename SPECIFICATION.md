# North Social Technical Specification

## 1. Abstract

This document specifies the Distributed Authenticated Repositories & Gossip (DARG) protocol, the technical foundation of the North Social network. The protocol is designed to enable a decentralized, performant, and censorship-resistant social media platform built upon a network of user-owned hardware.

## 2. Core Components

The network consists of two primary types of software entities:

*   **Home Node (HN):** An always-on, server-like application running on user-owned hardware (e.g., a single-board computer). The HN is the user's sovereign presence on the network. It hosts the user's data, manages P2P connections, participates in data distribution, and executes heavy computational tasks.
*   **Client Application (CA):** A lightweight application for user-facing platforms (mobile, desktop, web). The CA acts as a secure remote control for the user's HN. It is responsible for UI rendering and does not participate directly in P2P network operations.

## 3. Identity Layer

*   **Decentralized Identifiers (DIDs):** Each user account is controlled by a cryptographic key pair, which manages a W3C-compliant DID (e.g., `did:key`).
*   **DID Document:** The DID resolves to a signed document containing the user's public keys, a human-readable handle (e.g., `@username.can`), and the network address/ID of their HN.

## 4. Data Structure

*   **Personal Data Repository (PDR):** All of a user's data (posts, likes, follows, etc.) is stored in a local, cryptographically-signed, Merkle-tree-like data structure on their HN. Every action is a signed commit, creating a verifiable, tamper-proof history.

## 5. Data Distribution and Persistence

*   **Redundant Array of Independent Repositories (RAIR):** To ensure data availability when an HN is offline, PDR commits are sharded using erasure coding. An (n, k) scheme is used (e.g., 10 total shards, 5 required for reconstruction).
*   **Distributed Hash Table (DHT):** A Kademlia-based DHT is used for peer discovery and content addressing. The hashes of PDR data blocks and their corresponding shards are stored on the DHT, allowing peers to locate and retrieve data.
*   **Publish/Subscribe (PubSub):** A real-time messaging layer over the DHT is used for proactive timeline updates. HNs subscribe to the feeds of users they follow and receive new posts as they are published.

## 6. Performance Optimizations

*   **Proactive Feed Materialization:** HNs use the PubSub system to listen for new posts from followed accounts. They fetch, reconstruct, and store these posts in a local database in the background. The CA retrieves a pre-built timeline directly from its HN, resulting in near-instant load times.
*   **Optimistic UI Updates:** CAs update their UI immediately upon user action (like, reply) and send the command to the HN for asynchronous processing. This provides the perception of zero latency.
*   **Federated Caching:** Optional, community-run Relay Nodes can act as high-availability caches for popular data shards, accelerating retrieval times across the network.

## 7. Moderation

Moderation is a client-side, user-controlled function.

*   **Personal Block/Mute Lists:** Users can block or mute other users. This is a signed action in their PDR.
*   **Subscribable Moderation Lists:** Users can subscribe to public moderation lists published by other users or groups. The HN downloads these lists and pre-filters all incoming content before it is sent to the CA.

## 8. Search and Discovery

*   **Decentralized Indexing:** The protocol supports optional, opt-in Indexer Nodes. Users can grant trusted Indexers permission to crawl their public PDR data.
*   **Parallel Federated Queries:** CAs can be configured to query multiple independent Indexer Nodes simultaneously, merging the results to improve speed and resilience.
