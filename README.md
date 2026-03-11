# cpu-scheduling-with-game-theory
# Game-Theoretic CPU Scheduling Simulator

A C++ simulation that models CPU scheduling as a game theory problem,
where processes act as self-interested agents that can misreport their
burst times to gain scheduling advantage.

## Motivation

Standard scheduling algorithms like SJF assume processes report their
CPU burst times honestly. This project asks: what happens when processes
are selfish? Can a scheduler be designed to make honesty the optimal strategy?

## What it models

- **FCFS, Round Robin, SRT** — baseline schedulers (truthful agents)
- **Strategic SJF** — processes report multiplier × true burst (continuous strategy space)
- **Nash Equilibrium Solver** — best-response iteration with asymmetric incentive weighting
- **Repeated Game Dynamics** — COOPERATE / DEFECT / GRIM_TRIGGER / TIT_FOR_TAT strategies
- **VCG Penalty Mechanism** — charges liars for harm imposed on others
- **Discount Factor δ** — models how much agents value future vs present payoffs

## Key Results

| Scenario | Avg Slowdown | Price of Anarchy |
|---|---|---|
| SRT (social optimum) | 1.575 | 1.00 |
| FCFS (truthful) | 4.175 | 2.65 |
| Nash Equilibrium (no VCG) | 4.175 | 2.65 |
| Nash Equilibrium (with VCG) | 3.442 | 2.18 |

- Underreporting is a **dominant strategy** — everyone lies at equilibrium
- **One defector collapses cooperation** even with GRIM_TRIGGER punishment
- VCG reduces PoA from 2.65 → 2.18 but cannot fully enforce truthfulness in scheduling
- Critical δ\* = 1.0 — cooperation requires infinitely patient agents


Input format:
```
4
1  0  10
2  1   3
3  2   5
4  3   2
```
Each line: `ID  ArrivalTime  BurstTime`

## Concepts

Game Theory · Mechanism Design · Price of Anarchy · Nash Equilibrium ·
VCG Mechanism · Repeated Games · Grim Trigger · Tit-for-Tat ·
Normalised Slowdown · CPU Scheduling · Operating Systems
