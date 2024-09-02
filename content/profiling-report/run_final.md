---
title: "Profile simulation/base/@run_final function"
date: 2024-08-31
categories:
- GSoC 2024
---

The `run_final` function in total takes 6.811 seconds when ran on [tardis_example.yml](https://raw.githubusercontent.com/tardis-sn/tardis/master/docs/tardis_example.yml) without GPU. Here is the overall breakdown according to the cumulative time the other function takes: 

The average of 5 iterations was taken to write these profiling results. 

* [simulation/base/@iterate](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/simulation/base.py#L449) - 4.926 seconds - 1 calls
* [transport/montecarlo/base/MonteCarloTransportSolver/@run](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/base.py#L147) - 4.892 seconds - 1 calls
* [transport/montecarlo/numba_interface/@opacity_state_initialize](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/numba_interface.py#L151) - 1.884 seconds - 1 calls
* [spectrum/formal_integral/FormalIntegrator/@__init__](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/spectrum/formal_integral.py#L280) - 1.882 seconds - 1 calls
* [transport/montecarlo/base/@initialize_transport_state](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/base.py#L97) - 0.02776 seconds - 1 calls
* [transport/montecarlo/packet_source/BlackBodySimpleSource/@create_packet_nus](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/packet_source.py#L184)
* [opacities/opacity_solver/OpacitySolver/@solve](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/opacity_solver.py#L29) - 0.007204 seconds - 1 calls
* [model/geometry/radial1d/Homologous](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/model/geometry/radial1d.py#L169) - 0.007165 seconds - 1 calls
* [opacities/tau_sobolev/calculate_sobolev_line_opacity](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/tau_sobolev.py#L20) - 0.007026 seconds - 1 calls
* [model/geometry/radial1d/@r_inner_active](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/model/geometry/radial1d.py#L128) - 0.003652 seconds - 1 calls
* [model/geometry/radial1d/@r_outer_active](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/model/geometry/radial1d.py#L136) - 0.003043 seconds - 1 calls
* [opacities/opacity_state/@opacity_state_to_numba](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/opacity_state.py#L210) - 0.001976 seconds - 1 calls


Here is the breakdown of the `run_final` function according to the number of calls:

* [util/base/@update_packet_pbar](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/util/base.py#L662) - 100000 calls - 0.1052 seconds
* []
