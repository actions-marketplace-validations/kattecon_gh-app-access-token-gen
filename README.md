# Github App Access Token Generator

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

This Git repository contains a simple GitHub Action that generates a GitHub Access Token based upon specific inputs.

Access tokens are necessary in GitHub Actions when the built-in GITHUB_TOKEN does not provide the required permissions to perform certain actions.
The GITHUB_TOKEN in GitHub Actions, when used to perform
tasks, [will not trigger new workflow runs](https://docs.github.com/en/actions/using-workflows/triggering-a-workflow#triggering-a-workflow-from-a-workflow).
Because the GITHUB_TOKEN has limitations and cannot trigger new workflow runs in certain cases, actions that want to perform actions that trigger a workflow need to use a different token. An access token with the necessary permissions can be used for this purpose, and this action can be used to generate such a token.

The action takes in some inputs and uses them to create a token that can be used to interact with the GitHub API.

## Inputs

-   **app_id**: Required. Number. Github App Id - found in the app settings.
-   **private_key**: Required. String. The private key of the GitHub App in PEM format.
-   **installation_id**: Optional. Number. The ID of the app installation - found in url of the installation. If not provided, the default is the ID of an installation found using the repository input for the action.
-   **repository**: Optional. String. Repository name in the format owner/repo. Default value is the name of the current repository. The value is only used if **installation_id** is not provided. The repository is used to get the installation id for the app. It's expected the app is installed in the provided repository.

## Outputs

-   **token**: The generated GitHub Access Token.

## Rationale

The rationale behind this repository is to maintain simplicity and security at the forefront. It should be noted that the token generator may not be entirely suitable for all potential use cases due to limited flexibility. As a deliberate measure, customization options such as the utilization of custom GitHub URLs have been intentionally excluded. This decision was made based on the principle that less functionality translates to reduced testing and maintenance efforts, fewer bugs, and less susceptibility to security vulnerabilities.
