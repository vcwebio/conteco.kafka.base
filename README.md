# conteco.image.wrapper

The _conteco.image.wrapper_ image holds the common functionality wrapper for all __ContEco__ containers.

## Purpose

The _conteco.image.wrapper_ image is a store for all the common code-invariant functionality.  
Common functionality with a model dependent implementation is stored in the model images _conteco.model.*_.  
The wrapper image is used during the build process to inject the wrapper functionality into the newly build image.

## Common Functionality

This image is only concerned with common functionality that is code invariant.  
These APIs are organised in subfolders of the `bin` folder.  
The scripts in the `bin` folder itself can be overridden by any image.

### `bin` API

__`output-to-JSON`__  
This method provides the output from `stdout` to the JSON convertor when using the __ContEco__ JSON output format.  
By default no filter is applied. This can be overridden by all images. 

### `image` API

The `image` API contains two public methods for API method invocation:

__`.invoke`__  
This method invokes methods of the image specific API.
It adds the image specific API folder to the front of the `$PATH` for the duration of its execution.

__`.this`__  
This method copies the image specific `controlplane` API method to the repository root.
It is invoked by the `controlplane` instance which subsequently executes the method within its context.
The API methods are stored in the `/conteco/bin/image/controlplane` folder.
Image definitions are allowed to override the default implementation in situ.

It contains two method groupings for internal use: _general purpose_ and _executionplane_.  
[`image general purpose` API in detail](./docs/IMAGE-GENERAL-PURPOSE-API.md)  
[`image executionplane` API in detail](./docs/IMAGE-EXECUTIONPLANE-API.md) (coming soon)

### `image.controlplane` API

Coming soon.

### `image.wrapper` API

The wrapper API manages container interaction with stdin, stdout and stderr.  
It is accessible using command line flags when instantiating the image.  
[`image.wrapper` API Flags in detail](./docs/IMAGE-WRAPPER-API-FLAGS.md)
