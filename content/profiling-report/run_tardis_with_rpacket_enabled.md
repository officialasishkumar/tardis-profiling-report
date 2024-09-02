---
title: "Profile run_tardis function with r_packet tracking enabled"
date: 2024-09-02
categories:
- GSoC 2024
---

The `run_tardis` function in total takes 97.512 seconds when ran on [tardis_example.yml](https://raw.githubusercontent.com/tardis-sn/tardis/master/docs/tardis_example.yml) and r_packet tracking enabled without GPU. Here is the overall breakdown according to the cumulative time the other function takes: 

The average of 5 iterations was taken to write these profiling results. 

* [run_tardis](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/base.py#L11) - 97.512 seconds - 2/1 calls
    * [simulation/base/@run_convergence](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/simulation/base.py#L524) - 87.37 seconds - 1 calls
    * [simulation/base/@iterate](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/simulation/base.py#L449) - 87.32 seconds - 20 calls
    * [transport/montecarlo/base/@run](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/base.py#L147) - 78.31 seconds - 20 calls
    * [transport/montecarlo/packet_trackers/@rpacket_trackers_to_dataframe](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/packet_trackers.py#L166) - 22.85 seconds - 20 calls
    * [transport/montecarlo/base/@initialize_transport_state](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/base.py#L97) - 5.898 seconds - 20 calls
    * [simulation/base/@run_final](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/simulation/base.py#L553) - 5.701 seconds - 1 calls
    * [simulation/base/@from_config](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/simulation/base.py#L721) - 4.279 seconds - 1 calls
    * [plasma/assembly/legacy_assembly/@assemble_plasma](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/plasma/assembly/legacy_assembly.py#L5) - 2.827 seconds - 1 calls
    * [opacities/opacity_state/@opacity_state_to_numba](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/opacity_state.py#L210) - 2.456 seconds - 20 calls 
    * [transport/montecarlo/numba_interface/@opacity_state_initialize](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/numba_interface.py#L151) - 2.154 seconds - 1 calls
    * [spectrum/formal_integral/FormalIntegrator/@__init__](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/spectrum/formal_integral.py#L280) - 2.1538 seconds - 1 calls
    * [transport/montecarlo/packet_source/BlackBodySimpleSource/@create_packets](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/packet_source.py#L163) - 1.785 seconds - 20 calls
    * [transport/montecarlo/packet_source/BasePacketSource/@create_packets](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/packet_source.py#L59) - 1.784 seconds - 20 calls
    * [opacities/macro_atom/base/TransitionProbabilities/@calculate](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/macro_atom/base.py#L250) - 1.718 seconds - 21 calls
    * [opacities/macro_atom/base/TransitionProbabilities/@_calculate_transition_probability](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/macro_atom/base.py#L284) - 1.708 seconds - 21 calls
    * [simulation/base/Simulation/@advance_state](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/simulation/base.py#L274) - 1.514 seconds - 19 calls
    * [transport/montecarlo/base/MonteCarloTransportSolver/@from_config](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/base.py#L244) - 1.371 seconds - 1 calls
    * [plasma/properties/radiative_properties/BetaSobolev/@calculate](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/plasma/properties/radiative_properties.py#L133) - 1.097 seconds - 21 calls
    * [transport/montecarlo/estimators/radfield_mc_estimators/@initialize_estimator_statistics](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/estimators/radfield_mc_estimators.py#L7) - 1.039 seconds - 20 calls
    * [util/base/@update_packet_pbar](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/util/base.py#L662) - 1.015 seconds - 860000 calls
    * [model/geometry/radial1d/HomologousRadial1DGeometry/@to_numba](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/model/geometry/radial1d.py#L169) - 0.8638 seconds - 20 calls
    * [model/geometry/radial1d/HomologousRadial1DGeometry/@r_inner_active](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/model/geometry/radial1d.py#L128) - 0.3612 seconds - 99 calls
    * [model/base/SimulationState/@no_of_shells](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/model/base.py#L270) - 0.2761 seconds - 78 calls
    * [model/geometry/radial1d/HomologousRadial1DGeometry/@no_of_shells_active](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/model/geometry/radial1d.py#L166) - 0.2759 seconds - 78 calls
    * [transport/montecarlo/estimators/mc_rad_field_solver/MCRadiationFieldPropertiesSolver/@solve](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/estimators/mc_rad_field_solver.py#L30) - 0.267 seconds - 19 calls
    * [plasma/properties/radiative_properties/StimulatedEmissionFactor/@calculate](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/plasma/properties/radiative_properties.py#L70) - 0.2416 seconds - 21 calls
    * [transport/montecarlo/estimators/mc_rad_field_solver/MCRadiationFieldPropertiesSolver/estimate_jblues](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/estimators/mc_rad_field_solver.py#L90) - 0.2187 seconds - 19 calls
    * [opacities/opacity_solver/OpacitySolver/@solve](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/opacity_solver.py#L29) - 0.215 seconds - 20 calls
    * [opacities/tau_sobolev/@calculate_sobolev_line_opacity](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/tau_sobolev.py#L20) - 0.2108 seconds - 20 calls
    * [opacities/macro_atom/macroatom_solver/MacroAtomSolver/@solve](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/macro_atom/macroatom_solver.py#L83) - 0.1835 seconds - 20 calls
    * [opacities/macro_atom/macroatom_solver/MacroAtomSolver/@solve_transition_probabilities](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/macro_atom/macroatom_solver.py#L43) - 0.1812 seconds - 20 calls
    * [plasma/properties/ion_population/IonNumberDensity/@calculate](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/plasma/properties/ion_population.py#L338) - 0.1622 seconds - 21 calls
    * [transport/montecarlo/packet_source/BasePacketSource/@create_packet_nus](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/packet_source.py#L184) - 0.1617 seconds - 20 calls
    * [plasma/radiation_field/planck_rad_field/DilutePlanckianRadiationField/@calculate_mean_intensity](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/plasma/radiation_field/planck_rad_field.py#L58) - 0.1573 seconds - 39 calls
    * [opacities/tau_sobolev/TauSobolev/@calculate](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/tau_sobolev.py#L104) - 0.1451 seconds - 21 calls
