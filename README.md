# Temporary release branches from release tags

Recently GH introduced a change where tags are not considered valid when evaluating branch protection rules – read more about it in the [blog post].

Prior to this change environments could be configured with allowed branches pattern matching the release-tags:
<img width="674" alt="image" src="https://github.com/hanseartic/temporary_release_branches/assets/1752217/b99b9575-628b-4857-a098-9a8046aa8124">

That effectively allowed to use different secrets and guard deployments directly from creating releases. For now the only way is to create/update a matching **branch** every time a deployment to a specific environment should be done.

## How to still deploy from a release?
This repo provides two workflows that showcase how to create a temporary branch on release-event.

The temporary branch can be protected by repo's environment protection to guard deployments.

> ℹ️ `PAT` needed
> ----
> In order to successfully trigger the deployment workflow, the branch must be created with a [`PAT`][PAT] – pushing a branch with the github-actions token (`${{ github.token }}` or `$GITHUB_TOKEN`) [won't trigger][trigger] another workflow.

Therefore a secret named `PAT` (in this case) needs to be configured in the repo.

For showcasing, this repo has an environment named `release` configured to be deployable from branches following the pattern `v*.*.*`.


![release-branches480](https://github.com/hanseartic/temporary_release_branches/assets/1752217/30c03e48-fa34-4f96-9c67-876af9df9008)

[blog post]: https://github.blog/changelog/2023-08-10-actions-runs-triggered-from-tags-or-forks-with-the-same-name-as-a-protected-branch-will-now-be-blocked/
[PAT]: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
[trigger]: https://docs.github.com/en/actions/using-workflows/triggering-a-workflow#triggering-a-workflow-from-a-workflow
