---
title: "Profile transport/montecarlo/MonteCarloTransportSolver/@initialize_transport_state function"
date: 2024-09-10
categories:
- GSoC 2024
---

The `initialize_transport_state` function in total takes 0.02295 seconds when ran on [tardis_example.yml](https://raw.githubusercontent.com/tardis-sn/tardis/master/docs/tardis_example.yml) without GPU. Here is the overall breakdown according to the cumulative time the other function takes: 

The average of 5 iterations was taken to write these profiling results. 


| Function | Time (seconds) | Calls |
|----------|----------------|-------|
| [transport/montecarlo/MonteCarloTransportSolver/@initialize_transport_state](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/transport/montecarlo/base.py#L97) | 0.02295 | 1 |   