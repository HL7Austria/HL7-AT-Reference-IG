This Implementation Guide (IG) serves as a reference for all FHIR IGs developed within the Austrian healthcare domain.

To support consistency and clarity, three distinct categories of IGs have been defined: Base IGs, Framework IGs, and Use Case IGs. Each category follows its own set of guidelines, which are outlined on their respective reference pages.

## Mandatory and Optional Constraints 

Each category of Implementation Guide (IG) follows a defined mandatory structure, outlined in the corresponding templates. In addition, a set of optional tabs is available for use when relevant content is present in the IG. These optional elements are indicated using square brackets [ ].

For example, if the IG includes a CDA to FHIR mapping, the "Mapping" tab becomes applicable and should be included accordingly.

## IG Categories

Before creating your own IG, please determine which category best fits your use case and structure your guide accordingly. An overview of the categories is provided below:

### Base Implementation Guides
- Purpose: Define core FHIR elements, reusable data structures, constraints, extensions. 
- Examples: Country-specific base profiles, datatype constraints, terminology bindings.

#### Base IG Examples:

Below are some representative IGs that belong to this category:
- [HL7® Austria FHIR® Core Implementation Guide R4](https://fhir.hl7.at/r4-core-main/index.html)
- [HL7® Austria FHIR® Core Implementation Guide R5](https://fhir.hl7.at/r5-core-main/index.html)

### Framework Implementation Guides
- Purpose: Provide general-purpose architectural guidance, patterns, or infrastructure for building interoperable systems.

#### Framework IG Examples:
Below are some representative IGs that belong to this category*:
- [International Patient Summary Implementation Guide](https://build.fhir.org/ig/HL7/fhir-ips/)
- [Austrian Patient Summary (R4)](https://fhir.hl7.at/r4-ELGA-AustrianPatientSummary-main/index.html)
- [TC FHIR AG Scheduling R5](https://fhir.hl7.at/r5-TC-FHIR-AG-Scheduling-R5-main/index.html)
- [Structured Data Capture IG](https://build.fhir.org/ig/HL7/sdc/)

*note that these examples do not follow the specified guidelines for Austria.

### Use Case Implementation Guides
- Purpose: Solve a specific clinical or administrative need; typically implementable by stakeholders with defined workflows, possibly including APIs, operations, and example scenarios.

#### Use Case IG Examples:
Below are some representative IGs that belong to this category:
- [Moderne Patient:innenabrechnung und Datenkommunikation on FHIR (MOPED)](https://fhir.hl7.at/r5-ELGA-MOPED-main/index.html)
- [Integrierte Versorgung Herzinsuffizienz (R4)](https://fhir.hl7.at/r4-ELGA-IV-Herzinsuffizienz-main/index.html)
- [ELGA e-Medikation FHIR R5 Implementierungsleitfaden](https://fhir.hl7.at/r5-ELGA-e-medikation-main/index.html)
