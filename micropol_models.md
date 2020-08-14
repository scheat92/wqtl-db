# Models for micropollutants database

### `Chemical`
| Field             | Value    |
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
| Field                 | Value                                             |
|-----------------------|---------------------------------------------------|
| name                  | required as identical to `name` from `Chemical`   |
| smiles                | required as identical to `smiles` from `Chemical` |
| gist                  | required as `Y` or `N`                            |
| busan_water_authority | required as `Y` or `N`                            |
| keiti                 | required as `Y` or `N`                            |
| remark                | optional                                          |

* Currently, there are three institutes each of which has a different set of micropollutants for investigations. The number of institutions can be further increased by adding as many fields as required.
For brevity and convenience, each intitute is currently defined as `GIST`, `BWA` (Busan Water Authority), and `KEITI` the full description of which can be provided in Korean on the front-end, i.e., on a webpage.


### `Species`
| Field      | Value                              |
|------------|------------------------------------|
| name       | required as `name` from `Chemical` |
| net_charge | *                                  |
| identifier | *                                  |
| smiles     | *                                  |
| remark     | optional                           |

*To be automatically generated using a chemoinformatics library<br>
`Species` is to be used only as generated based on `name` and `smiles` provided in `Chemical`.
In other words, modifications/updates on the data except `remark` are neither required nor permitted.
Consider the data here as `read-only`.

### `PartitionCoefficient` (currently limits to octanol vs water?)
| Field                     | Value                                     |
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
| Field                     | Value                                     |
|---------------------------|-------------------------------------------|
| identifier                | required as `identifier` from `Species`   |
| value                     | required                                  |
| experimental_or_predicted | required as `experimental` or `predicted` |
| temp                      | required                                  |
| ph                        | required                                  |
| doi                       | required if relevant                      |
| url                       | required if relevant                      |
| remark                    | optional                                  |

### `MolarExtinctionCoefficient` (unit: /M/cm)
| Field                     | Value                                     |
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
| Field                     | Value                                     |
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
| Field                     | Value                                                                                                                                                                                                                                                      |
|---------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| reactant1                 | required as `identifier` from `Species` for `elementary` or `name` from `Chemical` for `apparent`                                                                                                                                                          |
| reactant2                 | required as `name` from `Chemical` for oxidants or `medium` from `Treatment` for physical treatments like UV, UV/H2O2                                                                                                                                      |
| value                     | required                                                                                                                                                                                                                                                   |
| unit                      | required most likely as `/M/s` or `/s`                                                                                                                                                                                                                     |
| experimental_or_predicted | required as `experimental` or `predicted`                                                                                                                                                                                                                  |
| elementary_or_apparent    | required as `elementary` or `apparent`                                                                                                                                                                                                                     |
| temperature               | required                                                                                                                                                                                                                                                   |
| ph                        | required if `apparent` is given                                                                                                                                                                                                                            |
| doi                       | required if relevant                                                                                                                                                                                                                                       |
| url                       | required if relevant                                                                                                                                                                                                                                       |
| remark                    | optional                                                                                                                                                                                                                                                   |
|                           | for ozonation, `ozone exposure` and `probe compound` e.g., indigo  and `water matrix`, e.g., milli-Q, wastewater, and `DOC` for wastewater, e.g., `ozone_exposure=0.0001Ms, probe_compound=indigo, water_matrix=milliQ, DOC=4.0mg/L` in case of wastewater |

### `AcidDissociationConstant`
| Field                     | Value                                     |
|---------------------------|-------------------------------------------|
| identifier                | required as `identifier` from `Species`   |
| value                     | required                                  |
| branching_ratio           | required                                  |
| experimental_or_predicted | required as `experimental` or `predicted` |
| temperature               | required                                  |
| doi                       | required if relevant                      |
| url                       | required if relevant                      |
| remark                    | optional                                  |

### `Treatment` (not implemented yet)
| Field     | Value                       |
|-----------|-----------------------------|
| medium    | required as UV, PAC, or GAC |
| property1 |                             |
| property2 |                             |
| property3 |                             |
| property4 |                             |
| property5 |                             |
| remark    | optional                    |