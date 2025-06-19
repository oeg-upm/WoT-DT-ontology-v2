# WoTDT: The WoT Digital Twin Ontology

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Version: 0.5.0](https://img.shields.io/badge/Version-0.5.0-blue.svg)](https://w3id.org/def/dtw#)

This is an ontology for defining Digital Twins and Semantic Digital Twins, as well as their aggregations, using W3C's Web of Things (WoT) standards. The objective is to provide a common vocabulary to describe the different dimensions of a Digital Twin, based on the `WoT Thing Description` specification.

## General Information

| Field | Value |
| --- | --- |
| **Version** | 0.5.0 |
| **Namespace** | `https://w3id.org/def/dtw#` |
| **Recommended prefix** | `dtw` |
| **Creator** | Salvador González Gerpe |
| **Contributors** | Andrea Cimmino, María Poveda Villalón, Raúl García Castro, Socorro Bernardos |
| **Dependencies** | `dcat3`, `wot-td` |

## Conceptual Model

The WoTDT ontology models a Digital Twin as an entity compatible with the Web of Things (WoT) ecosystem.

### The Digital Twin (`dtw:DigitalTwin`)

The central concept is `dtw:DigitalTwin`, which is defined as a specialization of `td:Thing` from the Web of Things standard. This allows any Digital Twin described with WoTDT to be directly compatible with the WoT ecosystem and its tools.

A `DigitalTwin` is composed of three main dimensions:

1.  **`dtw:PhysicalEntity`**: Represents the real-world physical asset that the twin digitizes. Each digital twin must be associated with **exactly one** physical entity.
2.  **`dtw:DigitalEntity`**: This is the container for all digital information and logic. A digital twin must have **at least one** of these entities.
3.  **`dtw:Connection`**: Defines the relationships and data flows between the different parts of the digital twin and with external systems.

### The Digital Entity (`dtw:DigitalEntity`)

The `dtw:DigitalEntity` class is the digital core and groups the following aspects:

* **Models (`dtw:Model`)**: Representations and abstractions of the system. The ontology defines a hierarchy of models to cover different needs:
    * Behavioral models (`dtw:BehavioralModel`).
    * Geometric models (`dtw:GeometricModel`).
    * Physical models (`dtw:PhysicalModel`).
    * Rules models (`dtw:RulesModel`).
    * Semantic models (`dtw:SemanticModel`), which in turn include ontologies (`dtw:OntologyModel`), mappings (`dtw:MappingModel`), and validations (`dtw:ShapesModel`).
* **Data (`dcat:Resource`)**: The twin's data, using the W3C DCAT vocabulary to describe datasets.
* **Services (`td:InteractionAffordance`)**: The interaction capabilities (properties, actions, and events) of the twin, directly reusing the WoT interaction model.

### Aggregation and Systems of Systems

WoTDT allows modeling complex systems through the aggregation of twins:

* **`dtw:DigitalTwinInstance`**: Represents a single, specific twin, linked to a physical asset.
* **`dtw:DigitalTwinAggregate`**: Represents a composition or "system of systems," formed by the aggregation of multiple `DigitalTwinInstance` and/or other `DigitalTwinAggregate`. This is achieved through properties like `dtw:aggregateDTwI` and `dtw:aggregateDTwA`.

### Connections

Connections are established through the `dtw:Connection` class, which links different `dtw:ConnectionPoint`. The classes `dtw:Model`, `dcat:Resource`, and `td:InteractionAffordance` can act as connection points, allowing for an explicit and well-defined flow of information between models, data, and services.

## How to Use

To use this ontology, import the following URI in your project: [https://w3id.org/def/dtw](https://w3id.org/def/dtw)

It is recommended to use the `dtw` prefix for the namespace.

## How to Cite

If you use this ontology in your work, please cite its authors.

```bibtex
@misc{wotdt,
  author = {Salvador González Gerpe and Andrea Cimmino and María Poveda Villalón and Raúl García Castro and Socorro Bernardos},
  title = {WoTDT: The WoT Digital Twin Ontology},
  year = {2023},
  version = {0.5.0},
  url = {https://w3id.org/def/dtw#}
}
```
