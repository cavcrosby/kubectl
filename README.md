# kubectl

Packaging for the `kubectl` Kubernetes client
(<https://github.com/kubernetes/kubernetes/tree/master/cmd/kubectl>).

## Installation

### Debian-like distributions

1. Update the `apt` package index and install packages needed to use the
   `kubectl` `apt` repository. The following steps assume that your `apt`
   package version is `2.3.10` or greater.

   ```shell
   sudo apt-get update
   sudo apt-get install --assume-yes "ca-certificates"
   ```

2. Install the `sources.list(5)` file for the `kubectl` `apt` repository.

   ```shell
   cat << _EOF_ | sudo tee "/etc/apt/sources.list.d/kubectl.sources"
   Types: deb
   URIs: https://cavcrosby.github.io/kubectl/deb
   Suites: all
   Components: main
   Architectures-Remove: i386
   Signed-By:
    -----BEGIN PGP PUBLIC KEY BLOCK-----
    .
    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
    =TVJp
    -----END PGP PUBLIC KEY BLOCK-----
   ```

3. Update the `apt` package index, then install `kubectl`.

   ```shell
   sudo apt-get update
   sudo apt-get install --assume-yes "kubectl"
   ```

## License

See LICENSE.
