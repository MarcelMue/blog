---
title: "Our Road to Cluster API Adoption"
date: 2020-11-21
hidden: true
---
At Giant Swarm, we manage Kubernetes clusters for our customers. That’s a lot of Kubernetes clusters — a whole lot. From early on, we invested heavily in automation to be able to handle this large lot of clusters efficiently. Our weapons of choice are Kubernetes operators, which we develop and run in our environments. These operators enable us to manage clusters in a fault-tolerant and highly resilient way.

There is a catch though: by building our own operators, we have introduced our own declarative API for cluster lifecycle management. This API is very different from approaches of other providers. Therefore, switching between different providers has become difficult for users.

Thankfully, the upstream [cluster API](https://github.com/kubernetes-sigs/cluster-api) project introduces a community-driven approach to a declarative Kubernetes-style API for cluster lifecycle management. In this talk, I’ll present our journey so far in building up our architecture with Kubernetes operators, as well as describe our progress and future vision of adopting the upstream cluster API.
