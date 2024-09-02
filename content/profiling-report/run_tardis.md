---
title: "Profile run_tardis function"
date: 2024-08-20
categories:
- GSoC 2024
---

The `run_tardis` function in total takes 64.94 seconds when ran on [tardis_example.yml](https://raw.githubusercontent.com/tardis-sn/tardis/master/docs/tardis_example.yml) without GPU. Here is the overall breakdown according to the cumulative time the other function takes: 

The average of 5 iterations was taken to write these profiling results. 

* [run_tardis](https://github.com/tardis-sn/tardis/blob/5fe6806d2dc18afa155ffeb3a3cb31518637a214/tardis/base.py#L11) - 64.94 seconds - 2/1 calls
    * [simulation/base/@iterate](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/simulation/base.py#L449) - 49.2 seconds - 20 calls
    * [simulation/base/@run_convergence](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/simulation/base.py#L524) - 45.61 seconds - 1 calls
    * [montecarlo/base/@run](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/transport/montecarlo/base.py#L147) - 42.34 seconds - 20 calls
    * [simulation/base/@run_final](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/simulation/base.py#L553) - 7.608 seconds - 1 calls
    * [simulation/base/@from_config](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/simulation/base.py#L721) - 5.392 seconds - 1 calls 
    * [plasma/base/@update](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/plasma/base.py#L183) - 2.758 - 21 calls
    * [plasma/properties/base/@update](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/plasma/properties/base.py#L98) - 2.741 seconds - 329 calls
    * [opacities/opacity_state/@opacity_state_to_numba](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/opacities/opacity_state.py#L210) - 2.212 seconds - 20 calls
    * [assemble_plasma](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/plasma/assembly/legacy_assembly.py#L5) - 2.162 seconds - 1 calls
    * [transport/montecarlo/numba_interface/@opacity_state_initialize](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/transport/montecarlo/numba_interface.py#L151) - 2.161 seconds - 1 calls
    * [spectrum/formal_integral/@__init__](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/spectrum/formal_integral.py#L280) - 2.160 - 1 calls
    * [plasma/assembly/base/@assemble](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/plasma/assembly/base.py#L587) - 2.094 seconds - 1 calls
    * [plasma/assembly/base/@__init__](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/plasma/assembly/base.py#L158) - 2.088 seconds - 2 calls
    * [io/util/@__new__](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/io/util.py#L192) - 2.047 seconds - 46 calls
    * [io/atom_data/base/@from_hdf](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/io/atom_data/base.py#L178) - 2.018 seconds - 1 calls
    * [io/model/parse_atom_data/@parse_atom_data](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/io/model/parse_atom_data.py#L9) - 2.017 seconds - 1 calls
    * [transport/montecarlo/BasePacketSource/@create_packets](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/transport/montecarlo/packet_source.py#L59) - 1.537 seconds - 20 calls
    * [transport/montecarlo/BlackBodySimpleSource/@create_packets](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/transport/montecarlo/packet_source.py#L163) - 1.537 seconds - 20 calls
    * [opacities/macro_atom/base/@calculate](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/opacities/macro_atom/base.py#L250) - 1.330 seconds - 21 calls
    * [opacities/macro_atom/base/@_calculate_transition_probability](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/opacities/macro_atom/base.py#L284) - 1.322 seconds - 21 calls
    * [simulation/base/@advance_state](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/simulation/base.py#L274) - 1.316 seconds - 19 calls
    * [transport/montecarlo/base/@from_config](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/transport/montecarlo/base.py#L244) - 1.152 seconds - 1 calls
    * [transport/montecarlo/estimators/radfield_mc_estimators/@initialize_estimator_statistics](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/transport/montecarlo/estimators/radfield_mc_estimators.py#L7) - 0.8927 seconds - 20 calls
    * [util/base/@update_packet_pbar](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/util/base.py#L662) - 0.8775 seconds - 860000 calls
    * [plasma/properties/radiative_properties/BetaSobolev/@calculate](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/plasma/properties/radiative_properties.py#L133) - 0.8392 seconds - 21 calls
    * [model/geometry/radial1d/HomologousRadial1DGeometry/@to_numba](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/model/geometry/radial1d.py#L169) - 0.7192 seconds - 20 calls 
    * [transport/montecarlo/configuration/base/@configuration_initialize](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/transport/montecarlo/configuration/base.py#L53) - 0.4018 seconds - 20 calls
    * [model/geometry/radial1d/@r_inner_active](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/model/geometry/radial1d.py#L127) - 0.2875 seconds - 99 calls
    * [opacities/marco_atom/transition_probabilities](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/opacities/macro_atom/transition_probabilities.py) - 0.2339 seconds - 1 calls
    * [transport/montecarlo/estimators/mc_rad_field_solve/@solve](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/transport/montecarlo/estimators/mc_rad_field_solver.py#L30) - 0.2304 seconds - 19 calls    

<br>

Here is the breakdown of the `run_tardis` function according to the number of calls:

* [util/base/@update_packet_pbar](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/util/base.py#L662) - 860000 calls - 0.5896 seconds
- [plasma/base/@get_value](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/plasma/base.py#L68) - 1260 calls - 0.001328 seconds
- check from 656 calls



