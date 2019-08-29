# conteco.image.wrapper

The __conteco.image.wrapper__ image holds the common functionality wrapper for all __ContEco__ containers.

## Purpose

The __conteco.image.wrapper__ image is a store for all the common code-invariant functionality.  
Common functionality with a model dependent implementation is stored in the model images __conteco.model.*__.  
The wrapper image is used during the build process to inject the wrapper functionality into the newly build image.

## Common Functionality

This image is only concerned with common functionality that is code invariant.

### Wrapper API

coming soon