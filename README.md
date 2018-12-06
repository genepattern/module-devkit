# GenePattern Module Development Kit

## Module Project Directory Layout
Here is a standard directory layout for a GenePattern module 

| file or folder | description | example |
| -------------- | ----------- | -------- |
| build.properties | module specific properties required to build and release the module |
| build.xml | ant build script required to build and release the module |
| docker/ | Docker folder, build the docker image here |
| docker/Dockerfile | the Dockerfile for the module |
| gpunit/ | GpUnit folder, put all test cases here |
| module/ | top level module folder, everything in here is added to the module.zip file |
| module/manifest | the manifest for the module |
| gp-mdk/ | aka 'module-devkit/', the module development kit added as a git subtree |

## Usage

### CLI
```markdown

# Usage:

    gp module [OPTIONS] [COMMAND]

# Options (from build.properties):

    module.name, default: lowercase directory name 
        In bash: `echo "${PWD##*/}" | tr '[:upper:]' '[:lower:]'`
        Example: dapple
    lsid.no_version, REQUIRED
        Example: urn:lsid:8080.gpbroad.broadinstitute.org:genepatternmodules:479
    lsid.version, REQUIRED
        Example: "0.19"
    build.id, default="", 
        Example: "-pre.3"
    tag, default: v${lsid.version}${build.id}
        Example: "v0.19-pre.3"
    dockerhub.organization, default: genepattern
    job.docker.image=${dockerhub.organization}/${module.name}:${tag}
        Example: "genepattern/dapple:v0.19-pre.3"

# Commands:

    build-image, create a docker image from the ./docker/Dockerfile
    build-zip,   create the module.zip file

# Commands wish list:

    tag-local,             create a snapshot release for testing locally
    tag-prerelease,        create a prerelease tag for testing on beta servers
    tag-release-candidate, create a release candidate tag
    tag-release,           create a production release tag
    
    install-local, install local module.zip on local server
    install-beta,  install module.zip on beta server
    
    test-in-container,  run gpunit tests directly in the docker container 
    test-local,         run gpunit tests in local gp server

    push-to-gparc, 
    push-to-repo, 

    release-local       build a module.zip for testing on a local GP server instance
    build-release-candidate  build a module.zip for testing on a beta GP server
    build-release            build a module.zip for deployment on a production GP server
    
    build-local-release
    build-prerelease
    build-release

```

# TODO
* combine with GpUnit, the mod-devkit and gpunit belong in the same project
* document job.docker.image=[organization/]repository[:tag] naming conventions
* document Semantic Versioning conventions and best practices
