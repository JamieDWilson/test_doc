---
layout: default
title: Changing Parameters
parent: Running OMG
nav_order: 2
---

The OMG function can take additional optional inputs to override any of the default parameters. This can be done in two ways: 1) directly in the function call and 2) via a pre-defined script. These options are *not* mutually exclusive!

## Defining parameters in the function call

These have to appear as pairs of 1) the parameter name as a string and 2) the parameter value. To make things easier to read, comment and edit, you can use the line-continuation (three dots: '...') to separate out the parameter inputs when writing a script. The advantage of this approach is that parameters can be altered easily and within loops.

For example, we can add a parameter name/value pair to define the name of the output directory to _basic_run_

```matlab
OMG(3000...
	,'gen_pars.save_output_directory','basic_run'... % name of experiment
	);
```

{: .note }
To make things easier to read, comment and edit, you can use the line-continuation (three dots: '...') to separate out the parameter inputs when writing a script. The advantage of this approach is that parameters can be altered easily and within loops.

We can change any number of parameters from their defaults in the same way:

```matlab
OMG(3000...
    	,'gen_pars.save_output_directory','basic_run'... % name of experiment
	,'bgc_pars.uptake_scheme','restoring'... % restore to PO4 observations
	,'bgc_pars.restore_timescale',30... % restoring timescale (days)
	,'bgc_pars.restore_data_file','PO4_Obs.mat'...	% observations
	,'bgc_pars.CARBCHEM_select',false... % turn off the carbon cycle
	);
```

{: .note }
Each new parameter name/value pair is followed by the line-continuation '...' and each new parameter line begins with a comma. This makes it easy to quickly delete a line or copy/paste a new line in.

## Defining parameters in a script

An alternative to changing parameter values in the function call is to pre-define them in a script that is read in when OMG initialises. This allows you to define a large set of parameters in one go and not have a long list of parameters defined in the function call. The files are kept in the _OMG/config_files_ directory. The script contains the same parameter name/value pairs but defined like normal MATLAB variables. The script name is then used as the value for the special _ocean\_config_ parameter:

You can include all the parameters from the previous example in a script called _new_setup_:

```matlab
gen_pars.save_output_directory			='basic_run';  	% name of experiment
bgc_pars.uptake_scheme				='restoring';  	% restore to PO4 observations
bgc_pars.restore_timescale			=30;  	       	% restoring timescale (days)
bgc_pars.restore_data_file			='PO4_Obs.mat'; % observations
bgc_pars.CARBCHEM_select			=false;  	% turn off the carbon cycle
```

You then point OMG to _new_setup_ in the function call:

```matlab
% Run OMG with default parameters with a number of different parameter values
OMG(3000...
	,'ocean_config','new_setup'...
	);
```

## Changing parameters in a script _and_ in the function call

Both options for setting parameters can be used simultaneously. For example, you can set values a larger number of parameters for an ensemble of experiments such as selection of tracers and then change specific parameters within the ensemble in the function call:

```matlab
% Run OMG with default parameters with a number of different parameter values
OMG(3000...
	,'ocean_config','new_setup',...
	,'bgc_pars.restore_timescale	',60,... 	% a weaker restoring timescale (days)
	);
```

##Relevant Parameters
1. _ocean_config_: name of script containing parameter values in OMG/config_files (string)


