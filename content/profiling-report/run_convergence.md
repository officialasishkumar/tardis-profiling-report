---
title: "Profile run_convergence function"
date: 2024-09-02
categories:
- GSoC 2024
---

The `run_convergence` ran on [tardis_example.yml](https://raw.githubusercontent.com/tardis-sn/tardis/master/docs/tardis_example.yml) without GPU. Here is the overall breakdown according to the cumulative time the other function takes: 

The average of 5 iterations was taken to write these profiling results. 

| Function                                                                                                                    | Time (seconds) | Calls  | Description                     |
|-----------------------------------------------------------------------------------------------------------------------------|----------------|--------|---------------------------------|
| [simulation/base/Simulation/@iterate](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/simulation/base.py#L449) | 40.21          | 19     | Lorem ipsum dolor sit amet.     |
| [transport/montecarlo/base/MonteCarloTransportSolver/@run](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/base.py#L147) | 33.61          | 3      | Consectetur adipiscing elit.    |
| [simulation/base/Simulation/@run_convergence](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/simulation/base.py#L524) | 6.828          | 2/1    | Integer nec odio.               |
| [transport/montecarlo/base/MonteCarloTransportSolver/@initialize_transport_state](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/base.py#L97) | 2.39           | 19     | Praesent libero.                |
| [opacities/opacity_state/@opacity_state_to_numba](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/opacity_state.py#L210) | 2.082          | 19     | Sed cursus ante dapibus diam.   |
| [transport/montecarlo/packet_source/BasePacketSource/@create_packets](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/packet_source.py#L59) | 1.593          | 19     | Sed nisi. Nulla quis sem.       |
| [transport/montecarlo/estimators/radfield_mc_estimators/@initialize_estimator_statistics](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/estimators/radfield_mc_estimators.py#L7) | 0.8161         | 19     | Nam quam nunc, blandit vel.     |
| [model/geometry/radial1d/HomologousRadial1DGeometry/@to_numba](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/model/geometry/radial1d.py#L169) | 0.7462         | 19     | Lorem ipsum dolor sit amet.     |
| [util/base/update_packet_pbar](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/util/base.py#L662) | 0.6757         | 760000 | Consectetur adipiscing elit.    |
| [model/geometry/radial1d/HomologousRadial1DGeometry](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/model/geometry/radial1d.py#L128) | 0.2599         | 95     | Integer nec odio.               |
| [transport/montecarlo/estimators/mc_rad_field_solver/MCRadiationFieldPropertiesSolver/@solve](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/estimators/mc_rad_field_solver.py#L30) | 0.2326         | 19     | Praesent libero.                |
| [transport/montecarlo/estimators/mc_rad_field_solver/MCRadiationFieldPropertiesSolver/@estimate_jblues](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/estimators/mc_rad_field_solver.py#L90) | 0.1965         | 19     | Sed cursus ante dapibus diam.   |
| [plasma/properties/radiative_properties/StimulatedEmissionFactor/@calculate](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/plasma/properties/radiative_properties.py#L70) | 0.1705         | 19     | Sed nisi. Nulla quis sem.       |
| [opacities/opacity_solver/OpacitySolver/@solve](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/opacity_solver.py#L29) | 0.1441         | 19     | Nam quam nunc, blandit vel.     |
| [opacities/tau_sobolev/@calculate_sobolev_line_opacity](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/tau_sobolev.py#L20) | 0.1405         | 19     | Lorem ipsum dolor sit amet.     |


Here is the overall breakdown according to the cumulative time the other function takes when r packet tracking is enabled:

| Function | Time (seconds) | Calls | Description |
|----------|----------------|-------|-------------|
| [simulation/base/Simulation/@iterate](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/simulation/base.py#L449) | 65.11 | 19 | cherry |
| [transport/montecarlo/base/MonteCarloTransportSolver/@run](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/base.py#L147) | 58.08 | 19 | cherry |
| [simulation/base/Simulation/@run_convergence](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/simulation/base.py#L524) | 23.3 | 2/1 | cherry |
| [transport/montecarlo/packet_trackers/@rpacket_trackers_to_dataframe](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/packet_trackers.py#L166) | 16.64 | 19 | cherry |
| [transport/montecarlo/base/MonteCarloTransportSolver/@initialize_transport_state](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/base.py#L97) | 2.446 | 19 | cherry |
| [opacities/opacity_state/@opacity_state_to_numba](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/opacity_state.py#L210) | 2.285 | 19 | cherry |
| [transport/montecarlo/packet_source/BasePacketSource/@create_packets](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/packet_source.py#L59) | 1.595 | 19 | cherry |
| [simulation/base/Simulation/@advance_state](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/simulation/base.py#L274) | 1.264 | 19 | cherry |
| [transport/montecarlo/estimators/radfield_mc_estimators](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/estimators/radfield_mc_estimators.py#L7) | 0.9259 | 19 | cherry |
| [model/geometry/radial1d/HomologousRadial1DGeometry/@to_numba](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/model/geometry/radial1d.py#L169) | 0.7514 | 19 | cherry |
| [util/base/update_packet_pbar](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/util/base.py#L662) | 0.6627 | 760000 | cherry |
| [plasma/base/BasePlasma/@update](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/plasma/base.py#L183) | 0.6491 | 19 | cherry |
| [transport/montecarlo/configuration/base/MonteCarloConfiguration/@configuration_initialize](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/configuration/base.py#L53) | 0.4336 | 19 | cherry |
| [model/geometry/radial1d/@r_inner_active](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/model/geometry/radial1d.py#L128) | 0.2697 | 95 | cherry |
| [model/geometry/radial1d/HomologousRadial1DGeometry/@no_of_shells_active](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/model/geometry/radial1d.py#L166) | 0.2173 | 76 | cherry |
| [model/base/SimulationState/@no_of_shells](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/model/base.py#L270) | 0.2172 | 76 | cherry |
| [transport/montecarlo/estimators/mc_rad_field_solver/MCRadiationFieldPropertiesSolver/@solve](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/estimators/mc_rad_field_solver.py#L30) | 0.2156 | 19 | cherry |
| [plasma/properties/radiative_properties/StimulatedEmissionFactor/@calculate](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/plasma/properties/radiative_properties.py#L70) | 0.1705 | 19 | cherry |
| [transport/montecarlo/estimators/mc_rad_field_solver/MCRadiationFieldPropertiesSolver/@estimate_jblues](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/estimators/mc_rad_field_solver.py#L90) | 0.1776 | 19 | cherry |
| [opacities/macro_atom/macroatom_solver/MacroAtomSolver/@solve](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/macro_atom/macroatom_solver.py#L83) | 0.1759 | 19 | cherry |
| [opacities/macro_atom/macroatom_solver/MacroAtomSolver/@solve_transition_probabilities](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/macro_atom/macroatom_solver.py#L43) | 0.1747 | 19 | cherry |
| [opacities/macro_atom/base/TransitionProbabilities/@_calculate_transition_probabilities](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/macro_atom/base.py#L48) | 0.1714 | 19 | cherry |
| [opacities/macro_atom/base/TransitionProbabilities/@_calculate_transition_probability](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/macro_atom/base.py#L110) | 0.1682 | 19 | cherry |
| [opacities/opacity_solver/OpacitySolver/@solve](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/opacity_solver.py#L29) | 0.1634 | 19 | cherry |
| [opacities/tau_sobolev/@calculate_sobolev_line_opacity](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/tau_sobolev.py#L20) | 0.1608 | 19 | cherry |
| [opacities/macro_atom/base/TransitionProbabilities/@_calculate_transition_probability](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/macro_atom/base.py#L284) | 0.1286 | 19 | cherry |
| [plasma/radiation_field/planck_rad_field/DilutePlanckianRadiationField/@calculate_mean_intensity](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/plasma/radiation_field/planck_rad_field.py#L58) | 0.1253 | 38 | cherry |
| [simulation/base/Simulation/@_get_convergence_status](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/simulation/base.py#L238) | 0.1151 | 19 | cherry |
| [transport/montecarlo/packet_source/BlackBodySimpleSource/@create_packet_nus](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/packet_source.py#L184) | 0.112 | 19 | cherry |
| [plasma/properties/ion_population/IonNumberDensity/@calculate](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/plasma/properties/ion_population.py#L338) | 0.1109 | 19 | cherry |
| [opacities/tau_sobolev/TauSobolev/@calculate](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/tau_sobolev.py#L104) | 0.0953 | 19 | cherry |