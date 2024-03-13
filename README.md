# githubdeployments-submodule-example

An example WordPress repository with a workflow script that installs Git submodules.

The [workflow](.github/workflows/wpcom.yml) does the following:

1. Checkout the repository
2. Tells the checkout task to fetch submodules with `submodules: true`
3. Tells GitHub to pass through the SSH key so that private submodules can also be fetched by specifying `ssh-key: ${{ secrets.SSH_PRIVATE_KEY }}`. 
    - Note: you don't need to create a secret. This is a secret that GitHub already has. By default, GitHub does not share secrets with actions so this line is necessary.
3. Create a build artifact with name `wpcom` which is required for WordPress.com's GitHub Deployment feature
