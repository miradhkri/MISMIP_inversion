# Description
Uses [EnsembleKalmanProcesses][1] alongside the [model-ensembler][2], to setup and test doing a WAVI inversion with the EKI machinery. 
Based off https://github.com/WAVI-ice-sheet-model/EKI_idealised_PIG-example/tree/main

- uses both volume (timeseries) and velocity (entire field) observations for the EKI update step
-	Uses a checkpoint file from the perfect simulation for the velocity masks, uses netcdf for the volume data, uses mat file for the velocity data. Used in generate_data.jl
-	Velocity from the end of the simulation, in this case t=200. To avoid double counting the velocity. That way, the inversion sees the velocity at the start of the simulation, the EKI sees the velocity at the end of the simulation
-	Using a checkpoint file from the perfect simulation in WAVI_driver.jl to load the model state before the inversion which contains things like the speed masks, the grid, etc.
-	Datamisfit controller is set to the default value of 1, to avoid ensemble convergence.
-	Peaks in terms of best matches to beta field and volumes at iteration 003 (4th iteration), and then gets worse. Overfitting and ensemble collapse? Implies datamisfit controller is too high. 




[1]: https://github.com/CliMA/EnsembleKalmanProcesses.jl
[2]: https://github.com/JimCircadian/model-ensembler
