# Upgrading Tanzu Application Platform

This document describes how to upgrade Tanzu Application Platform from 1.0 to 1.0.1.

You can perform fresh install of Tanzu Application Platform `1.0.1` by following the instructions in [Installing Tanzu Application Platform](install-intro.md).

## <a id='prereqs'></a>Prerequisites

Before you upgrade Tanzu Application Platform:

- Follow the instructions to [Install your Tanzu Application Platform profile](install.md#install-profile)
- Follow the instructions to [Install or update the Tanzu CLI and plug-ins](install-general.md#cli-and-plugin)
- Read through [Tanzu Application Platform GUI Considerations](tap-gui/upgrades.md#considerations)
- Verify all packages are reconciled by running `tanzu package installed list -A`

## Add new package repository

Follow these steps to add the new package repository:

1. Add the `1.0.1` version of the Tanzu Application Platform package repository by running:

    ```
    tanzu package repository update tanzu-tap-repository \
        --url registry.tanzu.vmware.com/tanzu-application-platform/tap-packages:1.0.1  \
        --namespace tap-install
    ```

1. Verify you have added the new package repository by running:

    ```
    tanzu package repository get tanzu-tap-repository --namespace tap-install
    ```

## Perform upgrade of Tanzu Application Platform

### Upgrade instructions for Profile-based installation

For Tanzu Application Platform that is installed by profile, you can perform the upgrade by running:

>**Note:** Ensure you run the following command in the directory where the `tap-values.yaml` file resides.

```
tanzu package installed update tap -p tap.tanzu.vmware.com -v 1.0.1  --values-file tap-values.yaml -n tap-install
```

### Upgrade instructions for component-specific installation

See additional information about [upgrading Tanzu Application Platform GUI](tap-gui/upgrades.html).

## Verify the upgrade

Verify the versions of packages after the upgrade by running:

```
tanzu package installed list --namespace tap-install
```