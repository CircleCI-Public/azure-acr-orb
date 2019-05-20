# Azure ACR Orb [![CircleCI status](https://circleci.com/gh/CircleCI-Public/azure-acr-orb.svg "CircleCI status")](https://circleci.com/gh/CircleCI-Public/azure-acr-orb) [![CircleCI Orb Version](https://img.shields.io/badge/endpoint.svg?url=https://badges.circleci.io/orb/circleci/azure-acr)](https://circleci.com/orbs/registry/orb/circleci/azure-acr) [![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/CircleCI-Public/azure-acr-orb/master/LICENSE) [![CircleCI Community](https://img.shields.io/badge/community-CircleCI%20Discuss-343434.svg)](https://discuss.circleci.com/c/orbs)
CircleCI orb for interacting with Amazon's Elastic Container Registry (ECR).

## Parameters
Following is the full list of parameters required by this orb's various commands and jobs. For details, see the [listing in the Orb Registry](https://circleci.com/orbs/registry/orb/circleci/azure-acr).

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `alternate-tenant` | `boolean` | `false` | Use an alternate tenant. Only applicable for user logins. |
| `attach-workspace` | `boolean` | `true` | Boolean for whether or not to attach to an existing workspace. |
| `azure-username` | `env_var_name` | `AZURE_USERNAME` | Environment variable storing your Azure username. Only applicable for user logins. |
| `azure-password` | `env_var_name` | `AZURE_PASSWORD` | Environment variable storing your Azure password. Only applicable for user logins. |
| `azure-sp` | `env_var_name` | `AZURE_SP` | Name of environment variable storing the full name of the Service Principal, in the form http://app-url. Only applicable for Service Principal logins. |
| `azure-sp-password` | `env_var_name` | `AZURE_SP_PASSWORD` | Name of environment variable storing the password for the Service Principal. Only applicable for Service Principal logins. |
| `azure-sp-tenant` | `env_var_name` | `AZURE_SP_TENANT` | Name of environment variable storing the tenant ID for the Service Principal. Only applicable for Service Principal logins. |
| `azure-tenant` | `env_var_name` | `AZURE_TENANT` | Environment variable storing your Azure tenant, necessary if `alternate-tenant` is set to true. Only applicable for user logins. |
| `checkout` | `boolean` | `true` | Boolean for whether or not to checkout as a first step. |
| `dockerfile` | `string` | `Dockerfile` | name of Dockerfile to use |
| `executor` | `executor` | `default` | name of any custom executor (default is `machine: true`) |
| `extra-build-args` | `string` | `""` | Extra flags to pass to `docker build` (see [docs.docker.com/engine/reference/commandline/build](https://docs.docker.com/engine/reference/commandline/build)) |
| `path` | `string` | `.` | path to Dockerfile, defaults to the working directory |
| `registry-name` | `string` |  N/A | name of your ACR registry |
| `repo` | `string` |  N/A | name of your ACR repository |
| `tag` | `string` |  `latest` | ACR image tag |
| `workspace-root` | `string` |  `.` | Workspace root path that is either an absolute path or a path relative to the working directory. |

## Usage
See below for a simple example of this orb's `build_and_push_image` job. For details, see the [listing in the Orb Registry](https://circleci.com/orbs/registry/orb/circleci/azure-acr).

### Simple
```yaml
version: 2.1

orbs:
  azure-acr: circleci/azure-acr@1.0.0

workflows:
  simple_build_and_push:
    jobs:
      # with default parameter values, the following would be sufficient to build and push an image to ACR
      - azure-acr/build_and_push_image:
		  registry-name: myRegistryName
		  login-server-name: myregistryname.azurecr.io
		  repo: myRepositoryName

```

## Contributing
We welcome [issues](https://github.com/CircleCI-Public/azure-acr-orb/issues) to and [pull requests](https://github.com/CircleCI-Public/azure-acr-orb/pulls) against this repository! For further questions/comments about this or other orbs, visit [CircleCI's Orbs discussion forum](https://discuss.circleci.com/c/orbs).
