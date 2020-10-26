# gds-generate-wiki-links
This action generates a wiki directory of deployed services in a GDS cluster

## Example Usage

```yml
name: Generate Wiki Links
on:
  push:
    branches:
      - $default-branch
jobs:
  generate-wiki-links:
    runs-on: ubuntu-20.04
    steps:
    - uses: actions/checkout@v2
      with:
        path: code

    - uses: actions/checkout@v2
      with:
        repository: ${{github.repository}}.wiki
        path: wiki

    - uses: actions/checkout@v2
      with:
        ssh-key: ${{secrets.GDS_DEPLOY_PRIVATE_KEY}}
        repository: glg/gds
        clean: true
        path: gds

    - uses: glg-public/gds-generate-wiki-links@main
      with:
        gds_repo: glg/gds
        cluster_name: i99
        cluster_version: v1
        git_username: "Generating Wiki Links"
        git_email: "githubdevopsuser@glgroup.com"
```
