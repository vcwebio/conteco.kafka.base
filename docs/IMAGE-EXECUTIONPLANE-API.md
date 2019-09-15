[`image.wrapper`](../README.md) >> `image executionplane` API

-----

# `image executionplane` API 

The methods are prefixed with `executionplane`.  
Execution logging methods used in the image and controlplane API method implementation.

__`executionplane`__  [method] [arguments]  
Takes as arguments a method + arguments for execution.  
It pipes the output of `stdout` and `stderr` as an `executionplane-message` of type INFO or ERROR respectively.
It is used for functionality where there is no control over the output.

__`executionplane-complete`__  
Executes `executionplane-message` with type _COMPLETED_.

__`executionplane-copied`__  [source >> destination]  
Executes `executionplane-message` with type _COPIED_ and includes source and destination if supplied.

__`executionplane-error`__  [error message]  
Executes `executionplane-message` with type _ERROR_ and includes error details if supplied.

__`executionplane-info`__  [information]  
Executes `executionplane-message` with type _INFO_ and includes information if supplied.

__`executionplane-invoke`__  [method] [arguments]  
Invokes a method with arguments.
It is used for methods that implement the executionplane API internally.
It doesn not allow recursive method calls.

__`executionplane-message`__  [type][message details]
Emits a message of [type] with [message details] if supplied.

__`executionplane-stderr`__  [INPUT]  
Reads the input buffer and outputs it as `executionplane-message`s of type _ERROR_.
Auxiliary method used by `executionplan`.

__`executionplane-stdout`__  [INPUT]  
Reads the input buffer and outputs it as `executionplane-message`s of type _INFO_.
Auxiliary method used by `executionplan`.

__`executionplane-transparent`__  [method] [arguments]  
Logs the execution of a command using the _COMMAND_ message type.
Executes the command without interfering with the output.

__`executionplane-warning`__  [warning details]  
Executes `executionplane-message` with type _WARNING_ and includes warning details if supplied.

-----
[`image.wrapper`](../README.md) >> `image executionplane` API
