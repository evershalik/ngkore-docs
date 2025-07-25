# Challenges in L1-L2 Interoperability within O-RAN

**Author:** [Shubham Kumar](https://www.linkedin.com/in/chmodshubham/)

**Published:** August 21, 2024

> _Part 1 of 3: xFAPI Series_

O-RAN (Open Radio Access Network) is a framework designed to emphasize interoperability and standardization, enabling baseband and radio unit components from different vendors to work together seamlessly. Despite its focus on modularity and open interfaces, the MAC-PHY interface, particularly FAPI, remains closed. This presents significant challenges in achieving true multi-vendor interoperability.

![alt text](./images/challenges-in-l1-l2-interoperability/fapi-interface.png)

## Vendor-Specific Challenges in L1-L2 Integration

Some L1 vendors, particularly those offering High-PHY solutions, design their software in a way that necessitates L2 (DU-High) and L3 (CU) vendors, who adhere strictly to 3GPP standards, to either modify their code to meet the specific requirements imposed by the L1 vendor or to use an additional intermediary component to ensure compatibility. For instance, Intel’s FlexRAN does not fully align with SCF standards, necessitating modifications to the L2-L3 code to maintain end-to-end connectivity. This often compromises 3GPP compliance, creating challenges in adhering to established standards.

### Role of Intermediary Components

In many cases, L2-L3 vendors opt to use intermediary components to maintain compliance with 3GPP standards and ensure smooth end-to-end connections. This approach is often preferred because modifying their code to align with specific L1 requirements not only complicates the integration process but also incurs additional costs and introduces potential interoperability issues with other L1 solutions. Moreover, each L1 vendor typically proposes a unique intermediary component, which can lead to vendor lock-in. For example, to achieve interoperability with Intel FlexRAN, OSC maintained an intermediary component, FAPI TM, to ensure connectivity.

### Proprietary APIs and Vendor Lock-In Risks

Even when L1 vendors comply with SCF standards and do not require intermediary components for connectivity, the risk of vendor lock-in persists due to vendor-specific APIs and software development environments. For instance, Nvidia’s Aerial platform includes its own software development tool, CUDA, which is an integral part of its proprietary ecosystem.

### Shared Memory Libraries and IPC Mechanisms

Additionally, each L1 vendor offers a unique inter-process communication (IPC) mechanism for message exchange at the FAPI or nFAPI interface. Nvidia's Aerial, for example, uses nvIPC, while Intel’s FlexRAN employs WLS; both are shared memory implementations used for communication with DU-High.

<br>

L2-L3 vendors aiming to demonstrate interoperability with multiple L1 solutions face the challenge of managing various intermediary components and shared memory libraries, each tailored to a different L1 vendor. This dependency significantly increases complexity and complicates efforts to maintain a seamless, multi-vendor, interoperable network environment.

![alt text](./images/challenges-in-l1-l2-interoperability/challenge-l2-l3.png)

## A Call for Industry Collaboration

The industry needs to collaborate and address this issue collectively to develop a solution that bridges the existing gap. In our next blog, we will explore how xFAPI tackles this challenge.
