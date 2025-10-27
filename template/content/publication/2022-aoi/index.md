---
title: "A Practical AoI Scheduler in IoT Networks with Relays"
date: 2022-03-08
publishDate: 2022-03-08
authors: ["Biplav Choudhury", "**Prasenjit Karmakar**", "Vijay K Shah", "Jeffrey H Reed"]
publication_types: ["3"]
abstract: "Internet of Things (IoT) networks have become ubiquitous as autonomous computing, communication and collaboration among devices become popular for accomplishing various tasks. The use of relays in IoT networks further makes it convenient to deploy IoT networks as relays provide a host of benefits, like increasing the communication range and minimizing power consumption. Existing literature on traditional AoI schedulers for such two-hop relayed IoT networks are limited because they are designed assuming constant/non-changing channel conditions and known (usually, generate-at-will) packet generation patterns. Deep reinforcement learning (DRL) algorithms have been investigated for AoI scheduling in two-hop IoT networks with relays, however, they are only applicable for small-scale IoT networks due to exponential rise in action space as the networks become large. These limitations discourage the practical utilization of AoI schedulers for IoT network deployments. This paper presents a practical AoI scheduler for two-hop IoT networks with relays that addresses the above limitations. The proposed scheduler utilizes a novel voting mechanism based proximal policy optimization (v-PPO) algorithm that maintains a linear action space, enabling it be scale well with larger IoT networks. The proposed v-PPO based AoI scheduler adapts well to changing network conditions and accounts for unknown traffic generation patterns, making it practical for real-world IoT deployments. Simulation results show that the proposed v-PPO based AoI scheduler outperforms both ML and traditional (non-ML) AoI schedulers, such as, Deep Q Network (DQN)-based AoI Scheduler, Maximal Age First-Maximal Age Difference (MAF-MAD), MAF (Maximal Age First) , and round-robin in all considered practical scenarios."
featured: false
publication: "ArXiv: 2203.04227"
links:
  - icon_pack: fas
    icon: scroll
    name: Link
    url: 'https://arxiv.org/abs/2203.04227'
---