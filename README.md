# qtile-silver &nbsp; [![bluebuild build badge](https://github.com/florianskarlax/qtile-silver/actions/workflows/build.yml/badge.svg)](https://github.com/florianskarlax/qtile-silver/actions/workflows/build.yml)

[qtile-silver](https://github.com/florianskarlax/qtile-silver) is a custom
Fedora-based OSTree image built with [blue-build](https://blue-build.org/).

## Features

This image includes both the [QTile](https://qtile.org/) window manager and 
the [GNOME](https://www.gnome.org/) desktop environment, for easier 
integration of GTK applications in QTile and having the option to switch to 
a more traditional desktop environment if needed.

## Installation

First install an OSTree-based Fedora image on your machine. I recommend
using the [Fedora Silverblue](https://silverblue.fedoraproject.org/) image,
but any OSTree-based image should work.

Then rebase to the latest image with the following command:

```shell
rpm-ostree rebase ostree-unverified-registry:ghcr.io/florianskarlax/qtile-silver:latest
systemctl reboot  # required to apply the new image
```

To get the latest signed image, you have to do the following step afterward:

```shell
rpm-ostree rebase ostree-image-signed:docker://ghcr.io/florianskarlax/qtile-silver:latest
systemctl reboot  # required to apply the new image
```

## ISO

I don't provide ISOs for this project due to the large size of the images,
but you can build your own ISO with the instructions available
[here](https://blue-build.org/how-to/generate-iso/).

## Building

To build the image locally, install [blue-build](https://blue-build.org/) and run:

```shell
bluebuild build ./recipes/recipe.yml
```

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s
[cosign](https://github.com/sigstore/cosign).
You can verify the signature by downloading the `cosign.pub` file from this 
repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/florianskarlax/qtile-silver
```

## Project Structure

- `recipes/` - Build recipes and common module configurations
- `files/` - System files, scripts, and GNOME schema overrides
- `modules/` - Custom blue-build modules

## Contributing

Contributions are welcome! If you have any ideas for new features or 
improvements, feel free to open an issue or submit a pull request.

## License

This project is licensed under the Apache License 2.0.
See the [LICENSE](LICENSE) file for details.
