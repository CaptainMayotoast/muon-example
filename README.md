## Muon build system example

### Getting started

#### Updating submodules (for the Docker image repo)

1. Run `git submodule update --init`

2. Run `git submodule update --recursive --remote` in the top level development folder (i.e. `/build`)

1. Build the C++ development container, run `cpp-development-container/gcc13/assemble_images_docker.sh`.

2. Enter the devcontainer with VS Code.

### Build

1. `muon setup -Db_staticpic=true -Dprefer_static=true -buildtype=debug debug`

2. `muon samu -C debug`


