# Github Action - Automatic Semantic Versioning
Here's an example of utilizing GitHub Actions for automated release branches.

This GitHub Actions workflow, `Scheduled Create Minor Release Branch`, is designed to automatically create a new release branch with an incremented minor version.

## Workflow Steps

1. **Checkout code**: This step checks out the code from the repository using the `actions/checkout` action. It fetches all branches and tags and retrieves only the `.github` directory for further steps.

2. **Get the latest tag**: This step fetches all the tags, finds the latest tag, and stores it in an environment variable named `last_tag`. This tag represents the last released version.

3. **Increment minor version**: In this step, the minor version is incremented by 1. The new version is stored in an environment variable named `version`.

4. **Create version tag**: The workflow sets up the necessary Git configurations and creates a new tag corresponding to the incremented version. The tag is annotated with a commit message indicating the version.

5. **Create release branch**: Finally, the workflow creates a new release branch with the format `release-X.Y.Z` where `X.Y.Z` represents the incremented version.

## Prerequisites

- Make sure the repository has the `.github` directory with the appropriate workflow file (e.g., `.github/workflows/create_minor_release_branch.yml`).

- Ensure that the repository has a valid Personal Access Token (PAT) with appropriate permissions to push tags and branches. The PAT should be added as a secret named `PAT_VERSION_RELEASE` in the repository.

## Environment Variables

The workflow uses the following environment variables:

- `last_tag`: Holds the last released version retrieved from the repository tags.

- `version`: Holds the incremented minor version that will be used to create the new release branch.

## Workflow Triggers

The workflow is triggered automatically based on the schedule defined in the `on` section of the workflow. It runs on a weekly basis, every Sunday, and handles the process of creating release branches automatically.

Please note that the workflow is optimized for repositories following semantic versioning conventions. The workflow incrementally increases the minor version for each release branch.

For any issues or questions related to this workflow, feel free to reach out to me.
