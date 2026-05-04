# OpenMarket
A fully decentralized, uncensorable, optionally anonymous marketplace that can’t be controlled, stopped, or shut down.

## Get the App
#### [OpenMarket Mobile App]() (coming soon)
#### [OpenMarket Desktop](https://github.com/lukeprofits/OpenMarket-Desktop) (coming soon)

## Tech
<li>IPFS</li>
<li>NOSTR</li>
<li>Monero</li>

## How it Works
```mermaid
flowchart TD
    subgraph "OpenMarket App"
        A[User creates Listing] 
        B[Create JSON + Upload to IPFS<br/>→ Get CID]
    end

    subgraph "Broadcast (Spread the CID)"
        C[Gossipsub<br/>libp2p]
        D[Bluetooth<br/>Local Announcement]
        E[Nostr<br/>Delayed Post]
        J[LoRA<br/>Local Announcement]
    end

    subgraph "The Swarm"
        F[Other OpenMarket Apps]
    end

    subgraph "Result"
        G[Everyone knows the CID]
        H[Everyone auto-pins & seeds the content]
        I[Fast loading from nearby peers]
    end

    A --> B
    B --> C
    B --> D
    B --> E
    B --> J

    C --> F
    D --> F
    E --> F
    J --> F

    F -->|"Hears and spreads new CIDs via Gossip, Bluetooth,<br/>and Nostr"| G
    G --> H
    H --> I

    B -.->|"Impossible to know who the original uploader was"| H

    style A fill:#4f46e5,stroke:#6366f1
    style B fill:#15803d,stroke:#4ade80
    style H fill:#166534,stroke:#86efac
    style I fill:#1e40af,stroke:#60a5fa
```
