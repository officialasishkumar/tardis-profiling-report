---
title: "Profile run_tardis function"
date: 2024-08-20
categories:
- GSoC 2024
---

The `run_tardis` function in total takes 64.94 seconds when ran on [tardis_example.yml](https://raw.githubusercontent.com/tardis-sn/tardis/master/docs/tardis_example.yml). Here is the overall breakdown according to the time the other function takes: 

* [run_tardis](https://github.com/tardis-sn/tardis/blob/5fe6806d2dc18afa155ffeb3a3cb31518637a214/tardis/base.py#L11) - 64.94 seconds
    * [run_final](https://github.com/tardis-sn/tardis/blob/5fe6806d2dc18afa155ffeb3a3cb31518637a214/tardis/simulation/base.py#L553) - 5.81 seconds
    * [run_convergence](https://github.com/tardis-sn/tardis/blob/5fe6806d2dc18afa155ffeb3a3cb31518637a214/tardis/simulation/base.py#L524) - 6.83 seconds
    * [iterate](https://github.com/tardis-sn/tardis/blob/5fe6806d2dc18afa155ffeb3a3cb31518637a214/tardis/simulation/base.py#L449) - 46.8 seconds
        * [run](https://github.com/tardis-sn/tardis/blob/5fe6806d2dc18afa155ffeb3a3cb31518637a214/tardis/transport/montecarlo/base.py#L147) - 39.4 seconds
        * [initialize_transport_state](https://github.com/tardis-sn/tardis/blob/5fe6806d2dc18afa155ffeb3a3cb31518637a214/tardis/transport/montecarlo/base.py#L97) - 7.28 seconds
    * [from_config](https://github.com/tardis-sn/tardis/blob/5fe6806d2dc18afa155ffeb3a3cb31518637a214/tardis/simulation/base.py#L721) - 6.33 seconds
        * [parse_atom_data](https://github.com/tardis-sn/tardis/blob/5fe6806d2dc18afa155ffeb3a3cb31518637a214/tardis/io/model/parse_atom_data.py#L9) - 2.49 seconds
        * [assemble_plasma](https://github.com/tardis-sn/tardis/blob/5fe6806d2dc18afa155ffeb3a3cb31518637a214/tardis/plasma/standard_plasmas.py#L55) - 2.35 seconds
        * [parse_simulation_state](https://github.com/tardis-sn/tardis/blob/5fe6806d2dc18afa155ffeb3a3cb31518637a214/tardis/io/model/parse_simulation_state.py#L7) - 0.0595 seconds



