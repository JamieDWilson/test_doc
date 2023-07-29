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
OMG(3000,...
	'gen_pars.save_output_directory','basic_run'... % name of experiment
	);
```



