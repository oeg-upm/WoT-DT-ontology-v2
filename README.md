# WoTDT: The WoT Digital Twin Ontology

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Version: 0.5.0](https://img.shields.io/badge/Version-0.5.0-blue.svg)](https://w3id.org/def/dtw#)

Esta es una ontología para definir Gemelos Digitales (Digital Twins) y Gemelos Digitales Semánticos, así como sus agregaciones, utilizando los estándares del Web of Things (WoT) del W3C. El objetivo es proporcionar un vocabulario común para describir las diferentes dimensiones de un Gemelo Digital, basándose en la especificación `WoT Thing Description`.

## Información General

| Campo | Valor |
| --- | --- |
| **Versión** | 0.5.0 |
| **Namespace** | `https://w3id.org/def/dtw#` |
| **Prefijo recomendado** | `dtw` |
| **Creador** | Salvador González Gerpe |
| **Colaboradores** | Andrea Cimmino, María Poveda Villalón, Raúl García Castro, Socorro Bernardos |
| **Dependencias** | `dcat3`, `wot-td` |

## Modelo Conceptual

La ontología WoTDT modela un Gemelo Digital como una entidad compatible con el ecosistema del Web of Things (WoT).

### El Gemelo Digital (`dtw:DigitalTwin`)

El concepto central es `dtw:DigitalTwin`, que se define como una especialización de `td:Thing` del estándar Web of Things. Esto permite que cualquier Gemelo Digital descrito con WoTDT sea directamente compatible con el ecosistema WoT y sus herramientas.

Un `DigitalTwin` se compone de tres dimensiones principales:

1.  **`dtw:PhysicalEntity`**: Representa el activo físico del mundo real que el gemelo digitaliza. Cada gemelo digital debe estar asociado a **exactamente una** entidad física.
2.  **`dtw:DigitalEntity`**: Es el contenedor de toda la información y lógica digital. Un gemelo digital debe tener **al menos una** de estas entidades.
3.  **`dtw:Connection`**: Define las relaciones y flujos de datos entre las diferentes partes del gemelo digital y con sistemas externos.

### La Entidad Digital (`dtw:DigitalEntity`)

La clase `dtw:DigitalEntity` es el núcleo digital y agrupa los siguientes aspectos:

* **Modelos (`dtw:Model`)**: Representaciones y abstracciones del sistema. La ontología define una jerarquía de modelos para cubrir diferentes necesidades:
    * Modelos de comportamiento (`dtw:BehavioralModel`).
    * Modelos geométricos (`dtw:GeometricModel`).
    * Modelos físicos (`dtw:PhysicalModel`).
    * Modelos de reglas (`dtw:RulesModel`).
    * Modelos semánticos (`dtw:SemanticModel`), que a su vez incluyen ontologías (`dtw:OntologyModel`), mapeos (`dtw:MappingModel`) y validaciones (`dtw:ShapesModel`).
* **Datos (`dcat:Resource`)**: Los datos del gemelo, utilizando el vocabulario DCAT del W3C para describir conjuntos de datos.
* **Servicios (`td:InteractionAffordance`)**: Las capacidades de interacción (propiedades, acciones y eventos) del gemelo, reutilizando directamente el modelo de interacción de WoT.

### Agregación y Sistemas de Sistemas

WoTDT permite modelar sistemas complejos mediante la agregación de gemelos:

* **`dtw:DigitalTwinInstance`**: Representa un gemelo individual y específico, vinculado a un activo físico.
* **`dtw:DigitalTwinAggregate`**: Representa una composición o un "sistema de sistemas", formado por la agregación de múltiples `DigitalTwinInstance` y/o otros `DigitalTwinAggregate`. Esto se logra a través de propiedades como `dtw:aggregateDTwI` y `dtw:aggregateDTwA`.

### Conexiones

Las conexiones se establecen a través de la clase `dtw:Connection`, que enlaza diferentes `dtw:ConnectionPoint`. Las clases `dtw:Model`, `dcat:Resource` y `td:InteractionAffordance` pueden actuar como puntos de conexión, permitiendo un flujo de información explícito y bien definido entre modelos, datos y servicios.

## Cómo Utilizar

Para utilizar esta ontología, importa la siguiente URI en tu proyecto: [https://w3id.org/def/dtw](https://w3id.org/def/dtw)

Se recomienda usar el prefijo `dtw` para el namespace.

## Cómo Citar

Si utilizas esta ontología en tu trabajo, por favor, cita a sus autores.

```bibtex
@misc{wotdt,
  author = {Salvador González Gerpe and Andrea Cimmino and María Poveda Villalón and Raúl García Castro and Socorro Bernardos},
  title = {WoTDT: The WoT Digital Twin Ontology},
  year = {2023},
  version = {0.5.0},
  url = {https://w3id.org/def/dtw#}
}
```