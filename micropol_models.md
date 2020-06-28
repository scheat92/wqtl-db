# Models for micropollutants database

### `Chemical`
| Field             | remark   |
|-------------------|----------|
| name              | required |
| abbreviation      | optional |
| casrn             | optional |
| smiles            | required |
| classification    | required |
| subclassification | optional |
| molecular_weight  | *        |
| molecular_formula | *        |
| remark            | optional |

*To be automatically generated using a chemoinformatics library<br>
Note that `Chemical` model contains not only micropollutants but also oxidants such as ozone, free chlorine (hypochlorous acid), etc.

### `TargetByInstitution`
| Field        | Remark                             |
|--------------|------------------------------------|
| name         | required as `name` from `Chemical` |
| institution1 | required or empty                  |
| institution2 | required or empty                  |
| institution3 | required or empty                  |
| remark       | optional                           |

* Currently, there are three institutes each of which has a different set of micropollutants for investigations. The number of institutions can be further increased by adding as many fields as required.
For brevity and convenience, each intitute is currently defined as `GIST`, `BWA` (Busan Water Authority), and `KEITI` the full description of which can be provided in Korean on the front-end, i.e., on a webpage.


### `Species`
| Field             | Remark                             |
|-------------------|------------------------------------|
| name              | required as `name` from `Chemical` |
| net_charge        | *                                  |
| identifier        | *                                  |
| smiles            | *                                  |
| is_representative | *                                  |
| remark            | optional                           |

*To be automatically generated using a chemoinformatics library<br>
`Species` is to be used only as generated based on `name` and `smiles` provided in `Chemical`.
In other words, modifications/updates on the data except `remark` are neither required nor permitted.
Consider the data here as `read-only`.

### `PartitionCoefficient` (currently limits to octanol vs water?)
| Field                     | Remark                                    |
|---------------------------|-------------------------------------------|
| identifier                | required as `identifier` from `Species`   |
| value                     | required                                  |
| experimental_or_predicted | required as `experimental` or `predicted` |
| temperature               | required                                  |
| ph                        | required                                  |
| doi                       | required if relevant                      |
| url                       | required if relevant                      |
| remark                    | optional                                  |

### `Solubility` (unit: mg/L)
| Field                     | Remark                                       |
|---------------------------|----------------------------------------------|
| identifier                | required from as `identifier` from `Species` |
| value                     | required                                     |
| experimental_or_predicted | required as `experimental` or `predicted`    |
| temp                      | required                                     |
| ph                        | required                                     |
| doi                       | required if relevant                         |
| url                       | required if relevant                         |
| remark                    | optional                                     |

### `MolarExtinctionCoefficient` (unit: /M/cm)
| Field                     | Remark                                    |
|---------------------------|-------------------------------------------|
| identifier                | required as `identifier` from `Species`   |
| value                     | required                                  |
| experimental_or_predicted | required as `experimental` or `predicted` |
| elementary_or_apparent    | required as `elementary` or `apparent`    |
| wavelength                | required                                  |
| temperature               | required                                  |
| ph                        | required                                  |
| doi                       | required if relevant                      |
| url                       | required if relevant                      |
| remark                    | optional                                  |

### `QuantumYield`
| Field                     | Remark                                    |
|---------------------------|-------------------------------------------|
| identifier                | required as `identifier` from `Species`   |
| value                     | required                                  |
| experimental_or_predicted | required as `experimental` or `predicted` |
| elementary_or_apparent    | required as `elementary` or `apparent`    |
| wavelength                | required                                  |
| temperature               | required                                  |
| ph                        | required                                  |
| doi                       | required if relevant                      |
| url                       | required if relevant                      |
| remark                    | optional                                  |

### `RateConstant`
| Field                     | Remark                                                 |
|---------------------------|--------------------------------------------------------|
| reactant1                 | required as identifier from `Species`                  |
| reactant2                 | required as identifier from `Species` or from `Medium` |
| value                     | required                                               |
| unit                      | required most likely as `/M/s` or `/s`                 |
| experimental_or_predicted | required as `experimental` or `predicted`              |
| elementary_or_apparent    | required as `elementary` or `apparent`                 |
| temperature               | required                                               |
| ph                        | required                                               |
| doi                       | required if relevant                                   |
| url                       | required if relevant                                   |
| remark                    | optional                                               |

### `AcidDissociationConstant`
| Field                     | Remark                                    |
|---------------------------|-------------------------------------------|
| acid                      | required as `identifier` from `Species`   |
| conjugate_base            | required as `identifier` from `Species`   |
| value                     | required                                  |
| experimental_or_predicted | required as `experimental` or `predicted` |
| temperature               | required                                  |
| doi                       | required if relevant                      |
| url                       | required if relevant                      |
| remark                    | optional                                  |

### `Medium` (not implemented yet)
| Field     | Remark                      |
|-----------|-----------------------------|
| medium    | required as UV, PAC, or GAC |
| property1 |                             |
| property2 |                             |
| property3 |                             |
| property4 |                             |
| property5 |                             |
| remark    | optional                    |