---
title: "Profile run_tardis function"
date: 2024-08-20
categories:
- GSoC 2024
---

The `run_tardis` function in total takes 64.94 seconds when ran on [tardis_example.yml](https://raw.githubusercontent.com/tardis-sn/tardis/master/docs/tardis_example.yml). Here is the overall breakdown according to the cumulative time the other function takes: 

The average of 5 iterations was taken to write these profiling results. 

* [run_tardis](https://github.com/tardis-sn/tardis/blob/5fe6806d2dc18afa155ffeb3a3cb31518637a214/tardis/base.py#L11) - 64.94 seconds - 2/1 calls
    * [iterate](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/simulation/base.py#L449) - 49.2 seconds - 20 calls
    * [run_convergence](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/simulation/base.py#L524) - 45.61 seconds - 1 calls
    * [montecarlo/run] (https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/transport/montecarlo/base.py#L147) - 42.34 seconds - 20 calls
    * [run_final](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/simulation/base.py#L553) - 7.608 seconds - 1 calls
    * [from_config](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/simulation/base.py#L721) - 5.392 seconds - 1 calls 
    * [plasma/update](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/plasma/base.py#L183) - 2.758 - 21 calls
    * [plasma/properties/update](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/plasma/properties/base.py#L98) - 2.741 seconds - 329 calls
    * [opacity_state_to_numba](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/opacities/opacity_state.py#L210) - 2.212 seconds - 20 calls
    * [assemble_plasma](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/plasma/assembly/legacy_assembly.py#L5) - 2.162 seconds - 1 calls
    * []



