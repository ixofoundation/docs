---
stoplight-id: k1s9a6azxoa4f
---

# ITMO-Vocabulary

The ITMO Vocabulary provides a formalized dictionary for semantic definitions of the Types of data used in ITMO Credentials.

This JSON-LD model defines the `ITMOCredential` class, extending schema.org’s "Intangible," to capture key information relevant to Internationally Transferred Mitigation Outcomes (ITMOs) under Article 6.2 of the Paris Agreement. 

Within a single context, it introduces properties for authorization details, quantification of NDC parameters (like greenhouse gases and sectors), and accounting measures such as corresponding adjustments. Other fields ensure environmental integrity by referencing IPCC methodologies and providing metrics or indicators to track progress. 

The model accommodates both single-year and multi-year NDC targets, includes temporal data on emissions trajectories, and supports validation by referencing a Party’s NDC and inventory reports. The flexible nature of these properties permits inclusion of numeric values (e.g., tonnes of CO2e), text references, and Boolean indicators, facilitating comprehensive tracking and documentation of ITMOs across different national systems.

*Note that the Context reference points to itself, allowing JSON-LD processors to correctly resolve "itmo" as a prefix within this context file. You can also include additional custom contexts or references if needed for cross-context relationships.*
