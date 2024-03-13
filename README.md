# githubdeployments-submodule-example

An example WordPress repository with a workflow script that installs Git submodules.

The [workflow](.github/workflows/wpcom.yml) does the following:

1. Checkout the repository
2. Tells the checkout task to fetch submodules with `submodules: true`
3. Provides a personal access token to access the private repo `token: ${{ secrets.REPO_PAT }}`. (see below)
3. Create a build artifact with name `wpcom` which is required for WordPress.com's GitHub Deployment feature

Note: if you have submodules are in a private repo, you will need to create a personal access token and then save that token as a secret in the repo where the workflow runs. 
1. Create a classic token here https://github.com/settings/tokens
   - Choose `repo` scope
2. Go to `https://github.com/:account/:repo/settings/secrets/actions` and save the token with a name like `REPO_PAT`.
3. In your workflow file, include `token: ${{ secrets.REPO_PAT }}` on the checkout action. See [here](https://github.com/Automattic/githubdeployments-submodule-example/blob/trunk/.github/workflows/wpcom.yml#L16). 
