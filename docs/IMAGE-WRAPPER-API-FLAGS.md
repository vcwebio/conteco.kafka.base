[`image.wrapper`](../README.md) >> `image.wrapper` API Flags

-----

# `image.wrapper` API Flags 

Scripts location: `/conteso/bin/image/wrapper`  
API to set the interaction with stdin, stdout and stderr of the container.

Behaviour and usage is also described in the help file, accessed using the `--help` flag.

## Behaviour without API Flags

The default output from `stdout` and `stderr` is in the __ContEco__ JSON format.  
The default action when the image is instantiated without commandline arguments is the execution of the default entry point.

If the first commandline argument doesn't match a flag, then it is interpreted as a bash command.

## Behaviour with API Flags

__`--base`__  
Indicates that any arguments that follow should be presented to the default entry point.
Default output format of `stdout` and `stderr` is in  __ContEco__ JSON format.
Can be preceded by the `--container` or `--interactive` flag.

__`--container`__  
Forces the output of `stdout` and `stderr` in  __ContEco__ JSON format.
It must be the first argument.
It can be combined with the `--base`, `--extract` and `--help` flags.

__`--extract`__  
Extracts the git repository to the `/conteco/pwd` folder which is usually mapped to a host or named volume.
Default output format of `stdout` and `stderr` is the standard format.
Can be preceded by the `--container` or `--interactive` flag.


__`--help`__  
Prints the help file to `stdout`.
Default output format of `stdout` and `stderr` is the standard format.
Can be preceded by the `--container` or `--interactive` flag.

__`--interactive`__  
Forces the output of `stdout` and `stderr` in  standard format.
It must be the first argument.
It can be combined with the `--base`, `--extract` and `--help` flags.


-----
[`image.wrapper`](../README.md) >> `image.wrapper` API Flags
