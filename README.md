#  GCP Workload Identity Configuration


This repository contains a [Crossplane configuration](https://docs.crossplane.io/latest/concepts/packages/#configuration-packages), tailored for users establishing their initial control plane with [Upbound](https://cloud.upbound.io). This configuration deploys fully managed Workload Identity related resources.

## Overview

The core components of a custom API in [Crossplane](https://docs.crossplane.io/latest/getting-started/introduction/) include:

- **CompositeResourceDefinition (XRD):** Defines the API's structure.
- **Composition(s):** Implements the API by orchestrating a set of Crossplane managed resources.

In this specific configuration, the AWS Network API contains:

- **an [WorkloadIdentity](/apis/definition.yaml) custom resource type.**
- **Composition of Workload Identity related resources:** Configured in [/apis/composition.yaml](/apis/composition.yaml)

This repository contains an Composite Resource (XR) file.

## Deployment

```shell
apiVersion: pkg.crossplane.io/v1
kind: Configuration
metadata:
  name: configuration-gcp-workload-identity
spec:
  package: xpkg.upbound.io/upbound/configuration-gcp-workload-identity:v0.15.0
```

## Testing

Run `make help.local` to get the up-to-date documentation for the testing
related targets, e.g

```shell
make help.local
e2e                            Run uptest together with all dependencies. Use `make e2e SKIP_DELETE=--skip-delete` to skip deletion of resources.
render                         Crossplane render
submodules                     Update the submodules, such as the common build scripts.
yamllint                       Static yamllint check
```

## Next steps

This repository serves as a foundational step. To enhance your control plane, consider:

1. create new API definitions in this same repo
2. editing the existing API definition to your needs


Upbound will automatically detect the commits you make in your repo and build the configuration package for you. To learn more about how to build APIs for your managed control planes in Upbound, read the guide on Upbound's docs.
