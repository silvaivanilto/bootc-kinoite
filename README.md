# BlueBuild Base Images Repo

This repo consists of base images maintained by the BlueBuild org and built with the BlueBuild CLI. These images come with batteries included and were modeled after the [Ublue Main Images](https://github.com/ublue-os/main) before they were reduced in scope. Thanks to [Ublue](https://universal-blue.org/) for giving us a good starting point!

## Images

| Recipe                                          | Image                                                        | Versions    |
|-------------------------------------------------|--------------------------------------------------------------|-------------|
| recipe/fedora-kinoite-nvidia-latest.yml         | ghcr.io/blue-build/base-images/fedora-kinoite-nvidia         | 43 (latest) |


## Installation

To rebase an existing atomic Fedora installation to the latest build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  bootc switch ghcr.io/blue-build/base-images/fedora-kinoite-nvidia:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  bootc switch --enforce-container-sigpolicy ghcr.io/blue-build/base-images/fedora-kinoite-nvidia:latest
  ```
- Reboot again to complete the installation
  ```
  systemctl reboot
  ```

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/blue-build/base-images/fedora-kinoite-nvidia:latest
```
