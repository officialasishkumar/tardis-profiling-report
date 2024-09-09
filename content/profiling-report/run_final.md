---
title: "Profile simulation/base/@run_final function"
date: 2024-08-31
categories:
* GSoC 2024
---

The `run_final` function in total takes 6.811 seconds when ran on [tardis_example.yml](https://raw.githubusercontent.com/tardis-sn/tardis/master/docs/tardis_example.yml) without GPU. Here is the overall breakdown according to the cumulative time the other function takes: 

The average of 5 iterations was taken to write these profiling results. 

| Function | Time (seconds) | Calls |
|----------|----------------|-------|
| [simulation/base/@iterate](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/simulation/base.py#L449) | 4.926 | 1 |
| [transport/montecarlo/base/MonteCarloTransportSolver/@run](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/base.py#L147) | 4.892 | 1 |
| [transport/montecarlo/numba_interface/@opacity_state_initialize](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/numba_interface.py#L151) | 1.884 | 1 |
| [spectrum/formal_integral/FormalIntegrator/@__init__](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/spectrum/formal_integral.py#L280) | 1.882 | 1 |
| [transport/montecarlo/base/@initialize_transport_state](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/base.py#L97) | 0.02776 | 1 |
| [opacities/opacity_solver/OpacitySolver/@solve](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/opacity_solver.py#L29) | 0.007204 | 1 |
| [model/geometry/radial1d/Homologous](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/model/geometry/radial1d.py#L169) | 0.007165 | 1 |
| [opacities/tau_sobolev/calculate_sobolev_line_opacity](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/tau_sobolev.py#L20) | 0.007026 | 1 |
| [model/geometry/radial1d/@r_inner_active](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/model/geometry/radial1d.py#L128) | 0.003652 | 1 |
| [model/geometry/radial1d/@r_outer_active](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/model/geometry/radial1d.py#L136) | 0.003043 | 1 |
| [opacities/opacity_state/@opacity_state_to_numba](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/opacity_state.py#L210) | 0.001976 | 1 |

Here is the overall breakdown according to the cumulative time the function takes when r packet tracking is enabled:

| Function | Time (seconds) | Calls |
|----------|----------------|-------|
| [simulation/base/@run_final](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/simulation/base.py#L553) | 6.659 | 2/1 |
| [simulation/base/@iterate](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/simulation/base.py#L449) | 4.736 | 1 |
| [transport/montecarlo/base/MonteCarloTransportSolver/@run](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/base.py#L147) | 4.733 | 1 |
| [transport/montecarlo/packet_trackers/@rpacket_trackers_to_dataframe](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/packet_trackers.py#L166) | 2.192 | 1 |
| [transport/montecarlo/numba_interface/@opacity_state_initialize](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/numba_interface.py#L151) | 1.923 | 1 |
| [spectrum/formal_integral/FormalIntegrator/@__init__](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/spectrum/formal_integral.py#L280) | 1.921 | 1 |
| [util/base/update_packet_pbar](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/util/base.py#L662) | 0.1034 | 100000 |
| [transport/montecarlo/base/@initialize_transport_state](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/base.py#L97) | 0.01974 | 1 |
| [transport/montecarlo/packet_source/BlackBodySimpleSource/@create_packets](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/transport/montecarlo/packet_source.py#L163) | 0.01128 | 1 |
| [transport/montecarlo/packet_source/BasePacketSource/@create_packets](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/transport/montecarlo/packet_source.py#L59) | 0.01123 | 1 |
| [opacities/opacity_solver/OpacitySolver/@solve](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/opacity_solver.py#L29) | 0.009432 | 1 |
| [opacities/tau_sobolev/calculate_sobolev_line_opacity](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/tau_sobolev.py#L20) | 0.009432 | 1 |

