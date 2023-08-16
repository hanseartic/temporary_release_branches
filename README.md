This repo provides two workflows that showcase how to create a temporary branch on release-event.

The temporary branch can be protected by repo's environment protection to guard deployments.

In order to successfully trigger the deployment workflow the branch must be created with a PAT - pushing a branch with the github-actions token won't trigger another workflow.
Therefore a secret named `PAT` needs to be configured in the repo.

For showcasing, this repo has an environment named `release` configured to be deployable from branches following the pattern `v*.*.*`.

