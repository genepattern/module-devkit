# GenePattern Module Development Kit

## Prerequisites
This development kit requires that you have the following software installed on your development machine:
* ant >= 1.8.1
* git
* GenePattern Server >= 3.9.11 for testing

The GenePattern Team uses the following external resources to share artifacts with the user community:
* github
* dockerhub

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

    build-local,      create a snapshot release for testing locally

    tag-prerelease,   create a prerelease tag
    tag-release,      create a production release tag
    
    install-local,    install local module.zip on local server
    install-beta,     install module.zip on beta server
    
    test-docker,      run gpunit tests directly in the docker container 
    test-local,       run gpunit tests in local gp server

    push-to-gparc, 
    push-to-repo, 

# Edit Module Commands:

    Use these commands to make edits directly to the manifest file. This is a proposed CLI alternative
    to the module integrator.
    
    create-module <module-name>     Initialize a project for a new module
    
    set-docker-image                Set the docker image
    set-command-line                Set the command line
    
    add-param  [PARAM_OPTIONS]      Add a new parameter
    edit-param [PARAM_OPTIONS]      Change a parameter

```

## Example docker commands
To build the docker image
```markdown
# template

    docker build -f Dockerfile . --tag {module-name}:v{module-version}

# examples

    docker build -f Dockerfile . --tag dapple
    docker build -f Dockerfile . --tag dapple:v0.19
    docker build -f Dockerfile . --tag genepattern/dapple:v0.19
```

## Links
* [dockerhub/genepattern dashboard](https://cloud.docker.com/u/genepattern)
* [GpUnit](https://github.com/broadinstitute/GpUnit)
* [Semantic Versioning](https://semver.org)
### Git
* [Git Basics](https://git-scm.com/book/en/v2/Getting-Started-Git-Basics)
* [git-scm.com](https://git-scm.com)

### Docker commands
* [Dockerfile COPY command](https://docs.docker.com/engine/reference/builder/#copy)
* [docker build](https://docs.docker.com/engine/reference/commandline/build)

# TODO
* combine with GpUnit, the mod-devkit and gpunit belong in the same project
* document job.docker.image=[organization/]repository[:tag] naming conventions
* document Semantic Versioning conventions and best practices
* DocOpt integration (http://docopt.org/)
