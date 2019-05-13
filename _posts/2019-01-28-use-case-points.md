---
title: "Use Case Points."
published: true
comments: true
---

### Use Case Points (UCP)

* ####  Unadjusted Use Case Weight (UUCW)

| Use Case Classification | No. of Transactions       | Weight     |
| ----------------------- | ------------------------- | ---------- |
| Simple                  | 1 to 3 transactions       | 5          |
| Average                 | 4 to 7 transactions       | 10         |
| Complex                 | 8 or more transactions    | 15         |


* #### Unadjusted Actor Weight (UAW)

| Actor Classification    | Type of Actor                                                                              | Weight     |
| ----------------------- | ------------------------------------------------------------------------------------------ | ---------- |
| Simple                  | External system that must interact with the system using a well-defined API                | 1          |
| Average                 | External system that must interact with the system using standard communication protocols  | 2          |
| Complex                 | Human actor using a GUI application interface                                              | 3          |

* #### Technical Complexity Factor (TCF)

  #### TCF = 0.6 + (TF/100)

| Factor    | Description                           | Weight     |
| --------- | ------------------------------------- | ---------- |
| T1        | Distributed system                    | 2.0        |
| T2        | Response time/performance objectives  | 1.0        |
| T3        | End-user efficiency                   | 1.0        |
| T4        | Internal processing complexity        | 1.0        |
| T5        | Code reusability                      | 1.0        |
| T6        | Easy to install                       | 0.5        |
| T7        | Easy to use                           | 0.5        |
| T8        | Portability to other platforms        | 2.0        |
| T9        | System maintenance                    | 1.0        |
| T10       | Concurrent/parallel processing        | 1.0        |
| T11       | Security features                     | 1.0        |
| T12       | Access for third parties              | 1.0        |
| T13       | End user training                     | 1.0        |

* #### Environmental Complexity Factor (ECF)

  #### ECF = 1.4 + (-0.03 x EF)

| Factor    | Description                                | Weight     |
| --------- | ------------------------------------------ | ---------- |
| E1        | Familiarity with development process used  | 1.5        |
| E2        | Application experience                     | 0.5        |
| E3        | Object-oriented experience of team         | 1.0        |
| E4        | Lead analyst capability                    | 0.5        |
| E5        | Motivation of the team                     | 1.0        |
| E6        | Stability of requirements                  | 2.0        |
| E7        | Part-time staff                            | -1.0       |
| E8        | Difficult programming language             | -1.0       |

  * #### Corresponding interpolation values (S) of Environmental Complexity Factor (ECF)

  | Result    | Interpolation value (S)  |
  | --------- | ------------------------ |
  | > 0       | 0.05                     |
  | > 1       | 0.1                      |
  | > 2       | 0.6                      |
  | > 3       | 1.0                      |

  * #### Experience Stability Estimate (ES)

  $$ES = \sum_{i=1}^8 S_i$$

  | Result    | Estimate duration (P - hours per use case point)    |
  | --------- | --------------------------------------------------- |
  | < 1       | 48                                                  |
  | >= 1      | 32                                                  |
  | >= 3      | 20                                                  |

* #### Unadjusted Use Case Weight (UUCW)

  #### UUCW = (Total No. of Simple Use Cases x 5) + (Total No. Average Use Cases x 10) + (Total No. Complex Use Cases x 15)

* #### Unadjusted Actor Weight (UAW)

  #### UAW = (Total No. of Simple Actors x 1) + (Total No. Average Actors x 2) + (Total No. Complex Actors x 3)

* #### Use Case Points (UCP)

  #### UCP = (UUCW + UAW) x TCF x ECF

* #### Estimate Effort (EE)

  #### EE = AUCPxP (Hours)

* #### Step by step Use Case Points Methods

  <img src="{{ '/assets/images/UseCasePointsMethod.png' | absolute_url }}" alt="" height="354px" width="700px">

* #### Review App Demo

  * #### Create New Project

  <img src="{{ '/assets/images/project.png' | absolute_url }}" alt="" height="537px" width="700px">

  * #### Use Case & Actor

  <img src="{{ '/assets/images/usecase.png' | absolute_url }}" alt="" height="537px" width="700px">

  * #### Technical Complexity Factor

  <img src="{{ '/assets/images/tcf.png' | absolute_url }}" alt="" height="537px" width="700px">

  * #### Environmental Complexity Factor

  <img src="{{ '/assets/images/ecf.png' | absolute_url }}" alt="" height="537px" width="700px">

  * #### Estimate Effort

  <img src="{{ '/assets/images/effort.png' | absolute_url }}" alt="" height="537px" width="700px">

* #### Source code
  [Use Case Points](https://github.com/qnDev/ktcnpm.20181/tree/master/UseCasePoint)

* #### References

  [1] [Use Case Points From Wikipedia](https://en.wikipedia.org/wiki/Use_Case_Points)

  [2] [Software cost estimation using use case points: Getting use case transactions straight](https://www.ibm.com/developerworks/rational/library/edge/09/mar09/collaris_dekker/index.html)

  [3] [UML - Use Case Diagrams](https://www.tutorialspoint.com/uml/uml_use_case_diagram.htm)
