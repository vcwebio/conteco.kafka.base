# conteco.image.wrapper

The _conteco.image.wrapper_ image holds the common functionality wrapper for all __ContEco__ containers.

## Purpose

The _conteco.image.wrapper_ image is a store for all the common code-invariant functionality.  
Common functionality with a model dependent implementation is stored in the model images _conteco.model.*_.  
The wrapper image is used during the build process to inject the wrapper functionality into the newly build image.

## Common Functionality

This image is only concerned with common functionality that is code invariant and default implementations.  
These APIs are organised in subfolders of the `/conteco/bin` folder.  
The scripts in the `bin` folder itself can be overridden by any image.

## `bin` API

Location: `/conteco/bin`

The methods in the `bin` folder can be reimplemented by any of the images.
The subfolders of the `bin` folder are owned by specific images.

__`output-to-JSON`__  
This method provides the output from `stdout` to the JSON convertor when using the __ContEco__ JSON output format.  
By default no filter is applied. This can be overridden by all images. 

__`controlplane` API grouping__  
This API contains the default implementation for the lifecycle methods of the _controlplane_, used by most images.  
These implementations are requested by the _controlplane_ instance for execution within its context.  
The implementations are removed after execution.

[`controlplane` API grouping in detail](./docs/IMAGE-CONTROLPLANE-API.md)  

## `image` API

Location: `/conteco/bin/image`

The `/conteco/bin/image` folder is the only folder added to the `$PATH` at container initialisation.
It contains two methods used for API method invocation:

__`invoke`__  
This method invokes methods of the image specific API.
It adds the image specific API folder to the front of the `$PATH` for the duration of its execution.

__`this`__  
This method copies the image specific `controlplane` API method to the repository root.
It is invoked by the `controlplane` instance which subsequently executes the method within its context.
The API methods are stored in the `/conteco/bin/image/controlplane` folder.
Image definitions are allowed to override the default implementation in situ.

## `image.executionplane` API

Location: `/conteco/bin/image/executionplane`

This folder contains methods for internal use of the public API implementation.
The methods are split in two method groupings: `general purpose` and `executionplane`.  

__`image general purpose` API__  
This contains useful auxiliary methods.

[`image general purpose` API in detail](./docs/IMAGE-GENERAL-PURPOSE-API.md)  

__`image executionplane` API__  
This grouping consists of a number of logging methods to report on execution progress.
 
[`image executionplane` API in detail](./docs/IMAGE-EXECUTIONPLANE-API.md)

## `image.wrapper` API

Location: `/conteco/bin/image/wrapper`

The wrapper API manages container interaction with stdin, stdout and stderr.  
It is accessible using command line flags when instantiating the image.

[`image.wrapper` API Flags in detail](./docs/IMAGE-WRAPPER-API-FLAGS.md)
