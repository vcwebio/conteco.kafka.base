[`image.wrapper`](../README.md) >> `image.wrapper` API Methods

-----

# `image.wrapper` API Methods 

Location: `/conteso/bin/image/wrapper`  
API to set the interaction with stdin, stdout and stderr of the container.

__`.profile`__  
Sets the commandline cursor to the current working directory _pwd_.

__`entrypoint`__  

It initialises the `CONTECO_EXECUTIONPLANE_BASEPATH` and `CONTECO_EXECUTIONPLANE_ORIGINALPATH` PATH environment variables used for switching.   
It sets `CONTECO_IMAGE` and initialises `CONTECO_EXECUTIONPLANE`.
There is a hook for `CONTECO_PREENTRYPOINT` used for image type specific initialisatio, e.g. by _controlplane.base_.  
It sets the `CONTECO_EXECUTIONTAG` if supplied as commandline argument.  
Finally, the _image.wrapper_ entry sets default or __ContEco__ JSON output according to the first flag used and hands execution over to `run-image`.  


__`extract`__  
An auxiliary method that extracts the git repository to `/conteco/pwd/$CONTECO_REALM/$CONTECO_ECOSYSTEM.$CONTECO_TYPE.$CONTECO_NAME`.

__`run-image`__  
This method selects the next processing step depending on the commandline arguments.  
It implements the __--extract__ and __--help__ flags, or executes commandline or default `CONTECO_ENTRYPOINT`.

__`to-JSON`__  
Auxiliary method to convert output from `stdout` and `stderr` into the __ContEco__ JSON output format.  
It uses the `output-to-JSON` to filter / reshape output if required. Default is output as is. This method can be overridden by any image definition.

-----
[`image.wrapper`](../README.md) >> `image.wrapper` API Methods
