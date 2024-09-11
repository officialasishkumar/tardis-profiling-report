---
title: "Profile single_packet_loop function"
date: 2024-09-11
categories:
- GSoC 2024
---


Here is the overall breakdown of `single_packet_loop` function when ran on [tardis_configv1_benchmark.yml](https://github.com/tardis-sn/tardis/blob/328ec77df73f151f2f0c51dc9a851a3d96c1c37d/benchmarks/data/tardis_configv1_benchmark.yml) without GPU.

The average of 5 iterations was taken to write these profiling results. 


| Function | Time (seconds) | Calls |
|----------|----------------|-------|
| [simulation/base/Simulation/@iterate](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/simulation/base.py#L449) | 33.82 | 1 |
| [transport/montecarlo/MonteCarloTransportSolver/@initialize_transport_state](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/transport/montecarlo/base.py#L97) | 3.957 | 1 |
| [simulation/base/@from_config](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/simulation/base.py#L721) | 3.421 | 1 |
| [io/atom_data/base/@from_hdf](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/io/atom_data/base.py#L178) | 2.221 | 1 |
| [transport/montecarlo/numba_interface/@opacity_state_initialize](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/numba_interface.py#L151) | 2.212 | 1 |
| [plasma/assembly/legacy_assembly/@assemble_plasma](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/plasma/assembly/legacy_assembly.py#L5) | 2.203 | 1 |
| [plasma/base/BasePlasma/@update](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/plasma/base.py#L183) | 2.12 | 2 |
| [plasma/properties/base/ProcessingPlasmaProperty/@update](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/plasma/properties/base.py#L98) | 2.117 | 44 |
| [opacities/opacity_state/@opacity_state_to_numba](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/opacity_state.py#L210) | 2.008 | 1 |
| [transport/montecarlo/packet_source/BasePacketSource/@create_packets](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/packet_source.py#L59) | 1.342 | 1 |
| [transport/montecarlo/packet_source/BlackBodySimpleSource/@create_packets](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/transport/montecarlo/packet_source.py#L163) | 1.340 | 1 |
| [transport/montecarlo/base/MonteCarloTransportSolver/@from_config](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/base.py#L244) | 1.149 | 1 |
| [opacities/macro_atom/base/TransitionProbabilities/@calculate](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/opacities/macro_atom/base.py#L250) | 1.133 | 2 |
| [opacities/macro_atom/base/TransitionProbabilities/@_calculate_transition_probability](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/macro_atom/base.py#L284) | 1.131 | 2 |
| [plasma/properties/radiative_properties/StimulatedEmissionFactor/@calculate](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/plasma/properties/radiative_properties.py#L70) | 0.8902 | 2 |
| [transport/montecarlo/estimators/radfield_mc_estimators/@initialize_estimator_statistics](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/estimators/radfield_mc_estimators.py#L7) | 0.8378 | 1 |
| [model/geometry/radial1d/HomologousRadial1DGeometry/@to_numba](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/model/geometry/radial1d.py#L169) | 0.6121 | 2 |
| [transport/montecarlo/configuration/base/@configuration_initialize](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/transport/montecarlo/configuration/base.py#L53) | 0.3878 | 1 |
| [io/configuration/config_reader/Configuration/@from_yaml](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/io/configuration/config_reader.py#L212) | 0.2202 | 1 |
| [io/configuration/config_reader/Configuration/@from_config_dict](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/io/configuration/config_reader.py#L232) | 0.2086 | 1 |
| [io/configuration/config_validator](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/io/configuration/config_validator.py#L86) | 0.2083 | 1 |
