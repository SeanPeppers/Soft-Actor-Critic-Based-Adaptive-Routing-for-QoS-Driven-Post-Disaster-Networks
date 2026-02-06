# Soft Actor-Critic Based Adaptive Routing for QoS-Driven Post-Disaster Networks

This repository contains the implementation of an intelligent routing framework designed for **Post-Disaster Networks (PDNs)**. Using **Soft Actor-Critic (SAC)** and other state-of-the-art Reinforcement Learning (RL) algorithms, the system dynamically routes packets through a stochastic network where node congestion and bandwidth fluctuate in real-time.

## 📌 Project Overview

In the wake of a disaster, network topologies become highly unstable. Standard routing protocols like GPSR often fail to account for dynamic Quality of Service (QoS) requirements such as latency, jitter, and throughput.

This project implements a custom **Gymnasium** environment (`RoutingEnv`) that simulates these stressors and provides a comparative analysis of:

* **Soft Actor-Critic (SAC)**: An off-policy actor-critic agent using maximum entropy RL for robust exploration.
* **Proximal Policy Optimization (PPO)**: An on-policy gradient method for stable policy updates.
* **Encore RL**: A Deep Q-Network (DQN) style implementation with target network updates.
* **GPSR (Baseline)**: Greedy Perimeter Stateless Routing based on physical coordinates.

## 🛠 Features

* **Stochastic Environment**: Simulates link failures, TTL (Time-to-Live) expirations, and dynamic congestion/bandwidth replenishment.
* **Hyperparameter Optimization**: Integrated **Optuna** studies for each agent to find the most efficient network architectures and learning rates.
* **Multi-Metric Evaluation**: Compares agents based on Success Rate, Round-Trip Time (RTT), Jitter (standard deviation of delay), and Throughput Proxy.
* **Dueling Critic Architecture**: Enhances the SAC agent by using Dueling Networks to better estimate state values.

## 🚀 Getting Started

### Prerequisites

```bash
pip install torch gymnasium numpy matplotlib pandas seaborn optuna sympy==1.12

```

### Installation

1. Clone the repository:
```bash
git clone git@github.com:SeanPeppers/Soft-Actor-Critic-Based-Adaptive-Routing-for-QoS-Driven-Post-Disaster-Networks.git
cd Soft-Actor-Critic-Based-Adaptive-Routing-for-QoS-Driven-Post-Disaster-Networks

```


2. Run the Jupyter Notebook:
```bash
jupyter notebook github_version_for_ICC_SAC.ipynb

```


## 📊 Environment Logic

The `RoutingEnv` represents the network as a graph where each node has:

* **Congestion level**: Higher congestion increases the probability of packet loss and adds to link latency.
* **Bandwidth**: Affects the throughput bottleneck of a successful path.

**Reward Function:**


## 📈 Results and Visualization

The notebook includes comprehensive visualization tools using `Seaborn` and `Matplotlib` to compare agent performance across 1000 test episodes:

* **Convergence Plots**: Tracks the "Best Average Reward" over training epochs.
* **Violin Plots**: Shows the distribution of RTT and Total Rewards.
* **Bar Charts**: Direct comparison of Success Rates between RL agents and the GPSR baseline.

## 📂 File Structure

* `github_version_for_ICC_SAC.ipynb`: The primary notebook containing environment definitions, agent classes, training loops, and evaluation logic.
* `models/`: (Generated after training) Directory containing saved `.pth` files for Actor and Critic networks.
