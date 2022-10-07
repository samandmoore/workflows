# Workflows

Reusable [GitHub Workflows][github_workflows_link].

## Quick Start

To get started add a workflow to an existing GitHub workflow or create a
new one.

### Release a Gem to GitHub Packages

Here's an example of how to create a workflow to publish a gem to GitHub
Packages.

```yaml
name: release

on:
  push:
    branches:
      - main
    paths:
      - lib/*/version.rb

jobs:
  publish:
    uses: samandmoore/workflows/.github/workflows/gem_release.yml@main
```

This workflow can also be used in a monorepo setup where you have your
gem located somewhere other than the root of the repo.

```yaml
publish:
  uses: samandmoore/workflows/.github/workflows/gem_release.yml@main
  with: 
    working_directory: 'path/to/<gem_name>'
    # if you release multiple gems within the same repo, you will want
    # to include a prefix to ensure the tags are unique
    # release_prefix: '<gem_name>'
```

[github_workflows_link]: https://docs.github.com/en/actions/learn-github-actions/workflow-syntax-for-github-actions
