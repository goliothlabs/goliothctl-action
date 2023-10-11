# goliothctl-action
Use goliothctl, the Golioth CLI, from your GitHub Actions

> :warning: This project is considered experimental and is not recommended for production use. Functionality may break at any time.

# Inputs

| Parameter | Description | Required |
| --- | --- | --- |
| apiKey | The API Key generated via goliothctl or web console | Yes | 
| projectId | Project ID to use | Yes |

If using Create Device action:

| Parameter | Description | Required |
| --- | --- | --- |
| deviceName | Device name | Yes |
| psk | Pre-shared key. Used as part of device authentication | No |
| pskId | Pre-shared key ID. Used as part of device authentication | No |
| deviceTag | Tag used to target a release | No |

If using Create Artifact action:

| Parameter | Description | Required |
| --- | --- | --- |
| file | File to use for artifact
| artifactVersion | Artifact semantic version | Yes |
| releaseArtifact | Artifact to use for release | Yes |

If using Create Release action:
| Parameter | Description | Required |
| --- | --- | --- |
| releaseArtifact | Artifact to use for release | Yes |
| releaseVersion | Release version to use for release | Yes |
| releaseTag | Tag used to target a release | Yes |

# ✨ Quickstart

The fastest way to use the CLI:

```yaml
- name: Setup Golioth CLI
  uses: goliothlabs/goliothctl-action@main
  with:
    apiKey: ${{ secrets.APIKEY }}
    projectId: ${{ secrets.PROJECTID }}

- name: List devices
  run: goliothctl device list
```

The primary action only requires a Golioth API Key and Project ID. Refer to the Golioth [documentation](https://docs.golioth.io/) for to generate an API Key and retrieve a Project ID. We recommend settings these values as [repository secrets](https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions).

# Additional Actions

There are 3 additional "create" actions currently supported for devices, artifacts and releases intended to be used as steps in CI.

```yaml
- name: Checkout
  uses: actions/checkout@v4
    
- name: Use goliothctl
  uses: goliothlabs/goliothctl-action@main
  with:
    apiKey: ${{ secrets.APIKEY }}
    projectId: ${{ vars.PROJECTID }}
    deviceName: #SOME_NAME#
    deviceTag: #SOME_TAG#
    file: #SOME_FILE#
    artifactVersion: #SOME_VERSION
    releaseArtifact: #SOME_ARTIFACT#
    releaseVersion: #SOME_VERSION
    releaseTag: #SOME_TAG#
```

Each step is optional, ex. only create a release.

