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
| [transport/montecarlo/packet_source/BlackBodySimpleSource/@create_packets](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/transport/montecarlo/packet_source.py#L163) | 0.01298 | 1 |
| [transport/montecarlo/packet_source/BasePacketSource/@create_packets](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/packet_source.py#L59) | 0.01297 | 1 |
| [transport/montecarlo/packet_source/BlackBodySimpleSource/@create_packet_nus](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/packet_source.py#L184) | 0.009915 | 1 |
| [model/geometry/radial1d/HomologousRadial1DGeometry/@to_numba](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/model/geometry/radial1d.py#L169) | 0.005615 | 1 |
| [opacities/opacity_state/@opacity_state_to_numba](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/opacity_state.py#L210) | 0.002686 | 1 |
| [model/geometry/radial1d/@r_outer_active](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/model/geometry/radial1d.py#L136) | 0.002673 | 1 |
| [model/geometry/radial1d/@r_inner_active](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/model/geometry/radial1d.py#L127) | 0.002424 | 1 |
| [transport/montecarlo/packet_source/BlackBodySimpleSource/@create_packet_radii](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/transport/montecarlo/packet_source.py#L168) | 0.0009461 | 1 |
| [transport/montecarlo/packet_source/BasePacketSource/@calculate_radfield_luminosity](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/transport/montecarlo/packet_source.py#L108) | 0.0006625 | 1 |
| [transport/montecarlo/configuration/base/@configuration_initialize](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/transport/montecarlo/configuration/base.py#L53) | 0.0006299 | 1 |
| [transport/montecarlo/packet_source/BlackBodySimpleSource/@create_packet_mus](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/transport/montecarlo/packet_source.py#L227) | 0.0004624 | 1 |
| [model/geometry/radial1d/HomologousRadial1DGeometry/@v_inner_boundary_index](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/model/geometry/radial1d.py#L90) | 0.0002338 | 5 |
| [model/geometry/radial1d/HomologousRadial1DGeometry/@v_inner_active](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/model/geometry/radial1d.py#L108) | 0.0001055 | 2 |
| [transport/montecarlo/packet_source/BlackBodySimpleSource/@create_packet_energies](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/transport/montecarlo/packet_source.py#L249) | 0.0001846 | 1 |
| [model/geometry/radial1d/HomologousRadial1dGeometry/@v_outer_boundary_index](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/model/geometry/radial1d.py#L99) | 0.0001614 | 5 |