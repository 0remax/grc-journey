## ISO/IEC 27001 Standards & ISMS Scoping

The architecture and implementation methodology of the ISO/IEC 27001 standard, focusing heavily on establishing an Information Security Management System (ISMS) and defining its operational scope.

Without an explicitly defined ISMS scope, security teams try to protect everything at once, leading to budget depletion, resource burnout, and compliance failure. ISO/IEC 27001 provides the internationally recognized framework to systematically secure sensitive assets, manage vulnerabilities, and prove compliance to stakeholders and regulators.

ISO/IEC 27001 is not a rigid checklist; it is a management tool governed by the Plan-Do-Check-Act (PDCA) cycle. Scoping defines the boundary, identifying which locations, processes, networks, and data types fall under the ISMS. For a fintech like OremaxPay, scoping dictates whether customer databases, mobile app source code, and third-party payment gateways are protected under the formal audit boundary.

### ISO/IEC 27001 Core Clauses

Modern ISO management system standards (such as ISO 9001) follow a uniform High-Level Structure (HLS) based on Annex SL, where Clauses 4 through 10 form the core, auditable requirements structured around the Plan-Do-Check-Act (PDCA) cycle.

#### Clause 4: Context of the Organization
* **Operating Environment**: Requires determining internal and external issues (such as via SWOT or PESTLE analysis) that impact the management system's intended results.
* **Interested Parties**: Identifies the needs and expectations of relevant stakeholders, including customers and regulators.
* **Scope and QMS Processes**: Defines the boundaries of the system and maps out the necessary processes.

#### Clause 5: Leadership
* **Top Management Commitment**: Demands active leadership, accountability, and promotion of a quality or risk-aware culture.
* **Policy**: Requires establishing, communicating, and maintaining a formal organizational policy.
* Roles and Responsibilities**: Ensures organizational roles, responsibilities, and authorities are clearly assigned and communicated

#### Clause 6: Planning
* **Risks and Opportunities**: Implements risk-based thinking to identify potential threats and positive opportunities.
* **Objectives**: Sets measurable goals aligned with the policy and plans actions to achieve them.
* Planning of Changes**: Manages how changes to the management system are introduced and executed.

#### Clause 7: Support
* **Resources**: Ensures the provision of necessary infrastructure, environment, and human resources.
* **Competence and Awareness**: Guarantees personnel are trained, competent, and aware of their impact on the system.
* **Communication and Documented Information**: Governs internal/external communication and the control of documented information

#### Clause &: Operation
* **Operational Planning and Control**: Plans and executes core processes required to meet product or service requirements.
* **Requirements & Design**: Manages customer requirements, external providers, design, and development.
* **Control of Outputs**: Oversees production, service provision, and nonconforming outputs.

#### Clause 9: Performance Evaluation
* **Monitoring and Measurement**: Tracks, measures, analyzes, and evaluates system performance.
* **Internal Audit**: Conducts scheduled internal audits to verify if the management system conforms to requirements.
* **Management Review**: Requires top management to periodically review the effectiveness of the system

#### Clause 10: Improvement
* **Nonconformity and Corrective Action**: Reacts to nonconformities, corrects issues, and eliminates root causes.
* **Continual Improvement**: Enhances the suitability, adequacy, and effectiveness of the management system over time

### ISMS Scope for OremaxPay

* Entity: **OremaxPay LTD**
* Headquarters: **Victoria Island, Lagos**
* Regulatory Scope: **CBN, NDPC, PCI-DSS**
* Classification: **Confidential GRC Audit**

#### 1. Executive Summary & Operational Context

OremaxPay anchors its operations in the bustling heart of Victoria Island, Lagos, serving as a vital bridge between unbanked merchants in Balogun Market and digital-first consumers across Nigeria. As a mid-sized fintech licensed by the Central Bank of Nigeria (CBN), the company processes upwards of two million mobile money transactions daily while maintaining strict compliance under the Nigeria Data Protection Act (NDPA).

The engine room of OremaxPay relies on a fault-tolerant microservices architecture capable of handling the erratic uptime and latency typical of West African telecommunications infrastructure. When a user initiates a transfer or merchant payment via USSD or the mobile app, the request hits a localized gateway integrated with the Nigeria Inter-Bank Settlement System (NIBSS). Transactions are tokenized instantly to prevent fraud, and settlement occurs in real-time or near-real-time across partner commercial banks. To mitigate downtime during fiber cuts or power outages on the mainland, OremaxPay utilizes a hybrid cloud model, keeping core routing logic redundant across multi-region edge servers.

**Core Mathematical Throughput Model**
System transaction processing efficiency `Q` modeled against network latency `L` and redundancy factor `R` follows the relation:

`Q = α × (1 - e^(-λL)) + βR`

Where `α` represents peak processing capacity (2M tx/day), `λ` represents packet loss decay, and `β` represents cloud edge fault tolerance.

#### 2. Governance, Risk, and Compliance (GRC) Oversight

Operating under the watchful eye of GRC frameworks requires an uncompromising approach to data architecture. OremaxPay isolates Personally Identifiable Information (PII) from transaction payloads. Customer names, National Identification Numbers (NIN), and Bank Verification Numbers (BVN) are encrypted at rest using AES-256 and stored in secure, geo-fenced vaults compliant with local data sovereignty mandates. The GRC team enforces continuous monitoring through automated compliance pipelines. Access to user data is governed by strict Role-Based Access Control (RBAC) and Zero-Trust principles, ensuring that even internal engineering teams cannot view raw customer credentials or transaction histories without multi-party authorization and audited cryptographic keys. Automated logging captures every access attempt, feeding directly into dashboards reviewed weekly by internal risk officers and external statutory auditors to satisfy both PCI-DSS standards and regulatory guidelines set by the Nigerian Data Protection Commission (NDPC).

#### 3. Detailed Scoping Statement

To establish clear regulatory boundaries and optimize audit resource allocation, OremaxPay defines its statutory audit and compliance boundary through explicit in-scope and out-of-scope parameters.

**Operational Scope and Asset Classification**

| Component / Asset | Classification | Operational Scope & Rationale |
| :--- | :--- | :--- |
| **Mobile Money Processing Pipeline** | `IN-SCOPE` | Encompasses the USSD gateway, NIBSS integration endpoints, mobile application backend APIs, tokenization engines, and real-time transaction routing systems handling financial flows. |
| **User Database Servers** | `IN-SCOPE` | Cloud-hosted infrastructure housing customer PII, encrypted vaults (NIN/BVN records), ledger balances, and KYC documentation subject to NDPC and CBN data governance mandates. |
| **Customer Support Channels** | `IN-SCOPE` | Ticketing systems, live chat databases, and call center logs that process, display, or archive customer PII, disputed transaction logs, and identity verification artifacts. |
| **Marketing & Admin Offices** | `OUT-OF-SCOPE` | Physical office spaces in Victoria Island used solely for marketing campaigns, HR administration, or non-technical management. Excluded because they process neither cardholder data nor core system telemetry. |

#### Scoping Rationale & Boundary Justification

The boundary defined above ensures that GRC audits focus intensely on assets where financial data or PII resides, transits, or is processed. Non-technical administrative environments are explicitly excluded to streamline compliance verification and maintain a laser-sharp focus on information security risk vectors.

### ISO/IEC 27001:2022 Control Themes and Risk Treatment Linkage

* **Organizational Controls (Clause 5)**: Encompasses policies, threat intelligence, information security roles, asset management, and supplier relationships, linking directly to the risk treatment plan by establishing governance baselines, assigning ownership for residual risks, and setting rules for third-party cloud vendors handling PII.

* **People Controls (Clause 6)**: Covers screening, terms of employment, awareness training, and disciplinary processes, mapping to the risk treatment plan by mitigating internal threat vectors, human error, and social engineering risks through mandatory security vetting and continuous staff education.

* **Physical Controls (Clause 7)**: Focuses on secure areas, physical entry controls, equipment security, and clear desk/screen policies, tying into the risk treatment plan by protecting localized edge servers, branch offices, and hardware assets against unauthorized physical access, theft, or environmental hazards.

* **Technological Controls (Clause 8)**: Addresses access rights, secure authentication, malware protection, network security, data masking, and logging, integrating with the risk treatment plan by deploying technical safeguards like AES-256 encryption, RBAC, and automated monitoring pipelines to neutralize digital vulnerabilities in mobile money pipelines.









