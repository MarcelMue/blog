---
title: "Testable Kubernetes Operators"
date: 2020-11-21
hidden: true
---
Kubernetes operators have been used more commonly throughout the Kubernetes community to automate workflows, manage applications and infrastructure. These usecases have produced complex operators which need to be tested properly to ensure that they are working as intended. Testing operators in practice has been a difficult task - unit tests can only cover a limited scope of logic (even with mocks like k8sfakeclient) and e2e tests (while offering a wider scope) are plagued by a common issue: flapping.

To understand why e2e tests for kubernetes operators are prone to flapping, we first need to understand what a kubernetes operator exactly is and which components it communicates with. The operator pattern shows us two reasons for the increased flappiness:

1. Hard dependencies on external components
2. Eventual consistency

Kubernetes offers some concepts to improve the stability of our operators. Finalizers to prevent most issues with missed deletion events and deletion inconsistencies. ResourceVersion as a way of preventing most race conditions between operators and finally the CR status as an effective means to failing fast during tests. Working on our own operators at giantswarm we additionally implemented some best practices to make testing more reliable:

- Always collect all possible logs during tests
- Do not wait more than a few seconds during reconciliation
- Do not get complacent about flapping, issues are often actual issues in your implementation.

Using these techniques and best practices, we were able to improve the reliability of our e2e tests massively. The goal of an easily and reliably testable kubernetes operator is unfortunately not quite reached yet.
