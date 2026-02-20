# Description
Uses [EnsembleKalmanProcesses][1] alongside the [model-ensembler][2], to set up and test the WAVI inversion using the MISMIP Ice1r example. Uses https://github.com/WAVI-ice-sheet-model/EKI_idealised_PIG-example/tree/main

- no checkpoint files used here, unlike in the velocity case: uses the .nc outfile from the perfect sim to get the volume data and use in the EKI comparison (same as velocity). It also uses the last .mat file from the perfect simulation (instead of a checkpoint file) to set up the model in WAVI_driver.jl. 
-	Datamisfitcontroller = 1, on_terminate=stop – originally was set to "continue" as the EKI felt the ensemble was in a good place after roughly 2 iterations and so the misfit cap was reached and parameters stopped updating. 
-	Builds the covariance matrix and noise etc the simple way from alex’s example, not the way shown in the EKP package example and what is done when we introduce velocity
-	Good match to volume data (better than when we include velocity) but not as good for the fields as when including the velocity obs (only up to iteration 3 or 4, after that the velocity one gets worse) 



[1]: https://github.com/CliMA/EnsembleKalmanProcesses.jl
[2]: https://github.com/JimCircadian/model-ensembler

