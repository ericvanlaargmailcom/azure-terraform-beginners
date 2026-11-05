# azure-terraform-beginners
Beginners Guide to Terraforming Azure stuff

## Linux image

The demo uses Ubuntu 24.04 LTS (x64, Generation 1), with standard security maintenance until May 2029.

Azure image: `Canonical:ubuntu-24_04-lts:server-gen1:latest`. The `latest` version stays within Ubuntu 24.04 LTS; it does not select a newer Ubuntu release.

The Gen1 image matches the existing VM configuration. Review `terraform plan` before applying this change to an existing deployment: changing the OS image can replace the VM. This is not an in-place OS upgrade.
