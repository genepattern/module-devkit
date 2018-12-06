GenePattern Module Development Kit

# Module Project Directory Layout
Here is a standard directory layout for a GenePattern module 

| file or folder | description | example |
| -------------- | ----------- | -------- |
| build.properties | module specific properties required to build and release the module |
| build.xml | ant build script required to build and release the module |
| docker/ | Docker folder, build the docker image here |
| docker/Dockerfile | the Dockerfile for the module |
| gpunit/ | GpUnit folder, put all test cases here |
| module/ | top level module folder, everything in her is added to the module.zip file |
| module/manifest | the manifest for the module |
| gp-mdk/ | aka 'module-devkit/', the module development kit added as a git subtree |

