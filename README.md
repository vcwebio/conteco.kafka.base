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

## `controlplane` Lifecycle API

Location: `/conteco/extract/controlplane`

Each image contains an image specific implementations for the controlplane lifecycle methods.  
These methods are executed within the context of the `controlplane` image and are extracted just prior to execution.
This is the reason why they are stored in the `extract` folder.  
Image definitions can amend these methods as required using the `controlplane.base` external and internal API.

[`controlplane` API grouping in detail](./docs/IMAGE-CONTROLPLANE-API.md)  

## `image` API

Location: `/conteco/bin/image`

The `/conteco/bin/image` folder is the only folder added to the `$PATH` at container initialisation.  
It contains the API method invocation handler and a number of auxiliary methods:

__`invoke`__  
This method invokes methods of the image specific API.  
It adds the image specific API folder to the front of the `$PATH` for the duration of its execution.

__`image general purpose` API__  
The general purpose API contains useful auxiliary methods.

[`image general purpose` API in detail](./docs/IMAGE-GENERAL-PURPOSE-API.md)  

## `image.executionplane` API

Location: `/conteco/bin/image/executionplane`

This folder contains methods for internal use for the public API implementation.  
It consists of a number of logging methods to report on execution progress.
 
[`image executionplane` API in detail](./docs/IMAGE-EXECUTIONPLANE-API.md)

## `image.wrapper` API

Location: `/conteco/bin/image/wrapper`

The wrapper API manages container interaction with stdin, stdout and stderr.  
It is accessible using command line flags when instantiating the image.

[`image.wrapper` API Flags in detail](./docs/IMAGE-WRAPPER-API-FLAGS.md)

[`image.wrapper` API Methods in detail](./docs/IMAGE-WRAPPER-API.md)
