1. Download and build the newest haddock. The build instructions are
in `README.md`. 

    git clone https://github.com/haskell/haddock.git
    cd haddock

    cabal sandbox init
    cabal sandbox add-source haddock-library
    cabal sandbox add-source haddock-api
    cabal install --dependencies-only
    cabal build

Then install the new haddock as `haddock.real`

    cp dist/build/haddock/haddock /some/bin/dir/haddock.real

2. Create a wrapper script named `haddock`:

    #!/bin/sh

    /some/bin/dir/haddock.real --hyperlinked-source "$@"

Don't forget to make it executable and put it in your path.

4. Download and build `standalone-haddock`:

    mkdir build-standalone-haddock
    git clone https://github.com/feuerbach/standalone-haddock.git
    cd standalone-haddock
    cabal build
    cp dist/build/standalone-haddock/standalone-haddock /some/bin/dir/

An example of how to use `standalone-haddock`:

    mkdir temp
    cd temp
    cabal get heredoc-0.2.0.0
    standalone-haddock -o doc heredoc-0.2.0.0

Then open `doc/heredoc/index.html` in your browser.
