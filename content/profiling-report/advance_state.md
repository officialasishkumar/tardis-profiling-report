---
title: "Profile advance_state function"
date: 2024-09-11
categories:
- GSoC 2024
---

The `advance_state` function in total takes 0.06935 seconds when ran on [tardis_example.yml](https://raw.githubusercontent.com/tardis-sn/tardis/master/docs/tardis_example.yml) without GPU. Here is the overall breakdown according to the cumulative time the other function takes: 

The average of 5 iterations was taken to write these profiling results. 


| Function | Time (seconds) | Calls |
|----------|----------------|-------|
| [simulation/base/Simulation/@advance_state](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/simulation/base.py#L274) | 0.06935 | 1 |
| [plasma/base/BasePlasma/@update](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/plasma/base.py#L183) | 0.03575 | 1 |
| [plasma/properties/base/@update](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/plasma/properties/base.py#L98) | 0.03508 | 15 |
| [model/base/SimulationState/@no_of_shells](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/model/base.py#L270) | 0.01342 | 4 |
| [model/geometry/radial1d/HomologousRadial1DGeometry/@no_of_shells_active](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/model/geometry/radial1d.py#L166) | 0.01341 | 4 |
| [model/geometry/radial1d/@r_inner_active](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/model/geometry/radial1d.py#L127) | 0.01338 | 4 |
|[transport/montecarlo/estimators/mc_rad_field_solver/MCRadiationFieldPropertiesSolver/@solve](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/estimators/mc_rad_field_solver.py#L30)| 0.009866 | 1 |
|[transport/montecarlo/estimators/mc_rad_field_solver/MCRadiationFieldPropertiesSolver/@estimate_jblues](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/transport/montecarlo/estimators/mc_rad_field_solver.py#L90)| 0.00947 | 1 |
|[plasma/properties/radiative_properties/StimulatedEmissionFactor/@calculate](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/plasma/properties/radiative_properties.py#L70) | 0.00938 | 1 |
| [plasma/properties/ion_population/IonNumberDensity/@calculate](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/plasma/properties/ion_population.py#L338) | 0.007314 | 1 |
| [simulation/base/Simulation/@_get_convergence_status](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/simulation/base.py#L238) | 0.006603 | 1 |
| [plasma/radiation_field/planck_rad_field/DilutePlanckianRadiationField/@calculate_mean_intensity](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/plasma/radiation_field/planck_rad_field.py#L58) | 0.006499 | 2 |
| [opacities/macro_atom/base/@calculate](https://github.com/tardis-sn/tardis/blob/b08981d7bb6bb7955e285ea8973361e3874079a2/tardis/opacities/macro_atom/base.py#L250) | 0.005941 | 1 |
| [opacities/tau_sobolev/TauSobolev/@calculate](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/tau_sobolev.py#L104) | 0.005737 | 1 |
| [opacities/macro_atom/base/TransitionProbabilities/@_calculate_transition_probability](https://github.com/tardis-sn/tardis/blob/be4ec9a4f9423392bc1aa4a6f3316267faa70093/tardis/opacities/macro_atom/base.py#L110) | 0.00566 | 1 |
| [simulation/base/Simulation/log_plasma_state](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/simulation/base.py#L591) | 0.005141 | 1 |
| [model/base/SimulationState/@t_radiative](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/model/base.py#L155) | 0.004315 | 1 |
| [util/base/@intensity_black_body](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/util/base.py#L294) | 0.0041 | 2 |
| [model/base/SimulationState/@dilution_factor](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/model/base.py#L137) | 0.002933 | 1 |
| [plasma/properties/ion_population/IonNumberDensity/@calculate_with_n_electron](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/plasma/properties/ion_population.py#L297) | 0.001948 | 5 |
| [plasma/properties/ion_population/PhiSahaLTE/@calculate](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/plasma/properties/ion_population.py#L57) | 0.001855 | 1 |
| [plasma/properties/partition_function/PartitionFunction/@calculate](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/plasma/properties/partition_function.py#L376) | 0.001827 | 1 |
| [plasma/properties/radiative_properties/BetaSobolev/@calculate](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/plasma/properties/radiative_properties.py#L133) | 0.001271 | 1 |
| [plasma/properties/partition_function/LevelBoltzmannFactorLTE/@calculate](https://github.com/tardis-sn/tardis/blob/260207cb7cee6829390d77fbf48de53843818f09/tardis/plasma/properties/partition_function.py#L42) | 0.0006863 | 1 |