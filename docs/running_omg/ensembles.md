---
layout: default
title: Running Ensembles
parent: Running OMG
nav_order: 6
---

# Running Ensembles 
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

OMG can be used to run an ensemble of experiments easily. All that needs to be done is to create an array of parameter values, place the OMG function call within a loop and index the array to get the parameter value. 

In this example, we setup an array of _e_-folding depths for POC remineralisation. We first run a spinup as a starting point for each experiment. We then create a loop within which we create a unique experiment name, call OMG and input the _e_-folding depth from the array of values:

```matlab
% define perturbed parameter array
efold_depth=linspace(50,3000,10);

% run a spinup
OMG(10000...
	,'gen_pars.save_output_directory','spinup'...
	);

% run the ensemble
for n=1:numel(efold_depth)

	filename=strcat('efold_exp_',num2str(n)); % unique experiment name
	
	OMG(3000...
    	,'gen_pars.save_output_directory',filename ... % exp. name
      ,'gen_pars.OMG_restart_select',true... % restart
	    ,'gen_pars.OMG_restart_file','spinup'... % restart experiment name
		  ,'bgc_pars.POC_eL1',efold_depth(n,1)... % parameter value from array
		);
end	
```

\vspace{5mm}
\textbf{\textit{\underline{Example: Parallel Ensemble varying 2 Parameters}}}

In this example, we create an ensemble varying two parameters simultaneously - in this case varying the biological uptake rate of PO$_{4}$ and the remineralisation length scale of POM and quantifying the impact on atmospheric CO$_2$.

 We can make use of the parallel toolbox in MATLAB to save time by changing 'for' to 'parfor'. We also want to be able to view the key output quickly so we load the output directly to the workspace and copy the atmospheric CO$_2$ concentration to an array. 
