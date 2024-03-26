# Plan

## 1. Technical specifications

Creating a high-quality specification for code involves clear definition of the requirements, functionalities, features, and constraints of the protocol before the actual coding begins. It serves as source documentation, a guide for developers and stakeholders to ensure that the final product meets the initial vision and requirements.

Architecture Overview: Provide a high-level overview of the protocol architecture, including major components and their interactions. Define every functionality along with its input and output requirements. To do this, you can use a framework of pre-conditions, post-conditions, and actions in a logical format as outlined in this guide.

Constraints: Outline any limitations such as time, budget, or technology, that could impact the development. Include major milestones and plans for future audits.

Dependencies: List any external systems, libraries, or services that your project will rely on.

Battle-Tested Code: Use battle-tested libraries like OpenZeppelin contracts whenever possible in order to minimize the error surface.

Contracts Flow Diagrams: Visualize how the smart contracts will interact with each other.

Development Toolchain: Specify the development, testing, deployment, and monitoring tools necessary for the project.

## 2. Threat Modeling

**System-wide Invariants**: Define invariants across the system using a logical format. These assertions, which are expected to always hold during execution, are critical for effective testing, auditing, and monitoring. Clarifying these immutable properties is essential for planning security requirements.

**Assess Integration Risks**: Evaluate the security risks associated with integrating other protocols. Consider the security measures of these protocols and establish contingency plans for potential failures or loss of availability, such as utilizing external oracles or yield protocols.

**Document Potential Threats**: Identify and document potential threats, drawing inspiration from the [ImmuneFi severity classification system](https://immunefi.com/immunefi-vulnerability-severity-classification-system-v2-3/). This process involves a thorough analysis of vulnerabilities and their possible impact on your system.
