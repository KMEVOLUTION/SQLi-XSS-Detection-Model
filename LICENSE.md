# SQLi-XSS Detection Model License

**Version 1.0**
**Effective Date:** [DATE]

Copyright © [YEAR] [YOUR NAME / ORGANIZATION]. All rights reserved.

This license governs the use, reproduction, modification, redistribution, and commercial exploitation of the SQLi-XSS Detection Model and its associated model artifacts.

The Model currently includes, but is not limited to:

```text
model.h5
token.pkl
```

and any modified, converted, fine-tuned, retrained, adapted, or derivative version based substantially on these artifacts.

---

## 1. Definitions

### 1.1 Model

“Model” means the SQLi-XSS Detection Model, including its trained weights, parameters, architecture-related artifacts, tokenizer, and other files distributed together with the Model.

### 1.2 Derivative Model

“Derivative Model” means any model, checkpoint, weights, parameters, adaptation, fine-tuned version, converted version, or other work substantially derived from the Model.

### 1.3 Non-Commercial Use

“Non-Commercial Use” means use that is not primarily intended for commercial advantage, monetary compensation, revenue generation, or delivery of a paid product or service.

Examples include:

* Academic research
* Educational use
* Personal experimentation
* Cybersecurity laboratory exercises
* Student projects
* Non-commercial benchmarking
* Internal evaluation or testing
* Proof-of-concept development that is not deployed commercially
* Research publication

### 1.4 Commercial Use

“Commercial Use” means any use of the Model or Derivative Model that directly or indirectly supports commercial activity, revenue generation, paid services, business operations, or commercial advantage.

Commercial Use includes, but is not limited to:

* Integration into a commercial product
* Integration into a paid cybersecurity service
* Software-as-a-Service (SaaS)
* Managed Security Service Provider (MSSP) services
* Security monitoring offered to customers
* Commercial API services
* Commercial Web Application Firewall products
* Intrusion detection or prevention products sold or licensed to customers
* Paid consulting services using the Model
* Redistribution as part of a commercial software package
* Use within products or services for which customers are charged
* Creating or selling Derivative Models based on this Model

---

## 2. Non-Commercial License Grant

Subject to compliance with this License, the Licensor grants you a limited, worldwide, non-exclusive, royalty-free license to:

* Download the Model
* Use the Model
* Run inference with the Model
* Evaluate the Model
* Conduct research using the Model
* Modify the Model
* Create Derivative Models
* Use the Model for educational purposes

provided that such activities are performed solely for **Non-Commercial Use**.

---

## 3. Redistribution for Non-Commercial Purposes

You may redistribute the Model or a Derivative Model for Non-Commercial Use provided that:

1. A copy of this License is included with the redistributed Model.
2. The original copyright notice is preserved.
3. You clearly indicate any modifications you have made.
4. You do not represent a modified version as an official release of the original Model.
5. The redistributed Model remains subject to terms that are at least as restrictive as this License regarding Commercial Use.

You may not remove or modify notices identifying the original Model or its authors.

---

## 4. Commercial Use

Commercial Use is **not granted under this License**.

Any individual, company, organization, or other entity wishing to use the Model or a Derivative Model for Commercial Use must obtain a separate commercial license from the Licensor.

Commercial licensing terms may include:

* License fees
* Subscription fees
* Revenue sharing
* Usage-based fees
* Enterprise licensing
* OEM licensing
* Deployment restrictions
* Support agreements
* Other mutually agreed commercial terms

To request a commercial license, please contact:

```text
Name / Organization: [KCMEVOLUTION]
```

Commercial permission is valid only when granted in writing by the Licensor.

---

## 5. Internal Evaluation by Commercial Organizations

Commercial or for-profit organizations may use the Model without obtaining a commercial license solely for:

* Internal research
* Internal testing
* Technical evaluation
* Benchmarking
* Proof-of-concept development

provided that the Model is not:

* Used in production
* Made available to customers
* Used to provide a paid service
* Integrated into a revenue-generating product
* Used as part of a customer-facing security system

Moving from internal evaluation to production or customer-facing deployment requires a separate commercial license.

---

## 6. Derivative Models

You may create Derivative Models for Non-Commercial Use.

Derivative Models remain subject to the Commercial Use restrictions in this License.

Creating a Derivative Model does not automatically grant the right to use that Derivative Model commercially.

Commercial use of a Derivative Model requires authorization from the Licensor unless otherwise agreed in writing.

---

## 7. Model Outputs

The Licensor does not claim ownership over individual classification results generated through inference using the Model.

For example:

```text
Normal
SQL Injection
XSS
```

and associated confidence scores may be used by the user subject to applicable law and other agreements.

However, using Model Outputs as part of a commercial product or service may constitute Commercial Use of the Model and may therefore require a commercial license.

---

## 8. Attribution

For publications, research projects, derivative repositories, or redistributed copies of the Model, users should provide reasonable attribution to the original project.

Suggested attribution:

```text
SQLi-XSS Detection Model
Bi-LSTM-based model for detecting SQL Injection and Cross-Site Scripting payloads.
```

Where practical, include a link to the original repository or model page.

---

## 9. No Warranty

THE MODEL IS PROVIDED “AS IS” WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED.

THE LICENSOR MAKES NO WARRANTIES REGARDING:

* ACCURACY
* RELIABILITY
* FITNESS FOR A PARTICULAR PURPOSE
* SECURITY
* AVAILABILITY
* NON-INFRINGEMENT
* DETECTION OF ALL ATTACKS
* ABSENCE OF FALSE POSITIVES
* ABSENCE OF FALSE NEGATIVES

Machine-learning-based cybersecurity detection systems may produce incorrect classifications.

Users are responsible for evaluating the Model before deploying it in any environment.

---

## 10. Security Disclaimer

The Model is intended to assist in detecting web payloads associated with:

* SQL Injection
* Cross-Site Scripting
* Normal traffic

The Model should not be considered a complete cybersecurity solution.

It should not be relied upon as the sole mechanism for preventing or detecting attacks.

Users are encouraged to combine the Model with other security mechanisms such as:

* Secure coding practices
* Input validation
* Parameterized SQL queries
* Output encoding
* Web Application Firewalls
* Intrusion Detection Systems
* Security monitoring
* Logging
* Human security analysis

---

## 11. Limitation of Liability

TO THE MAXIMUM EXTENT PERMITTED BY APPLICABLE LAW, THE LICENSOR SHALL NOT BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, CONSEQUENTIAL, OR EXEMPLARY DAMAGES ARISING FROM THE USE OR INABILITY TO USE THE MODEL.

THIS INCLUDES, WITHOUT LIMITATION:

* SECURITY INCIDENTS
* DATA LOSS
* DATA BREACHES
* BUSINESS INTERRUPTION
* LOST PROFITS
* FALSE POSITIVE DETECTIONS
* FALSE NEGATIVE DETECTIONS
* UNDETECTED ATTACKS
* SYSTEM FAILURE

Use of the Model is at the user's own risk.

---

## 12. Prohibited Representation

You may not:

* Claim that your modified Model is an official release of the original project.
* Use the name of the original author or organization to imply endorsement without written permission.
* Misrepresent the origin of the Model.
* Remove copyright or licensing notices from redistributed copies.

---

## 13. Third-Party Materials

This License applies only to rights held by the Licensor.

The Model may have been developed using third-party datasets, libraries, frameworks, or other materials that remain subject to their respective licenses and terms.

Users are responsible for complying with any applicable third-party licenses.

This License does not grant rights that the Licensor does not own or have authority to license.

---

## 14. Termination

Your rights under this License automatically terminate if you materially violate its terms.

Upon termination, you must cease unauthorized use and distribution of the Model.

The Licensor may separately authorize continued use through a written commercial or other license agreement.

---

## 15. Separate Commercial Agreement

A commercial license may provide additional rights beyond those granted under this License.

If there is a conflict between this License and a separately executed commercial agreement, the commercial agreement will govern the activities covered by that agreement.

---

## 16. Reservation of Rights

All rights not expressly granted under this License are reserved by the Licensor.

Nothing in this License grants ownership of the Model to the user.

---

## 17. Acceptance

By downloading, accessing, using, modifying, or distributing the Model, you acknowledge that you have read and understood this License and agree to comply with its terms.

If you do not agree with these terms, you must not use or distribute the Model.

---

## Commercial Licensing Contact

For commercial licensing, enterprise deployment, OEM integration, or other commercial usage requests:

```text
[KCMEVOLUTION / KCMEVOLUTION]
```
