# maybe-not
Close issues and/or pull requests for repositories, randomly, upon submission.

## Disclaimer

This GitHub Action, while functional, is written only for satirical purpose, and
should not be used in collaborative repositories.  Collaborative programming,
especially open source, is a beautiful thing and both contributors and maintainers
should be treated respectfully for donating their time to improve projects.  Please
do not use this GitHub Action in bad faith.

## Usage

You can change the response comment message using the `message` option. The default
response comment message is:

`Sorry, fate has decided that this one isn't happening.`

You can toggle the rate at which the action will respond to issues and/or pull
requests using the `fail-percentage` option, which you can set from 0-100 (default
is 5).

You can toggle responding to issues and pull requests individually by using the
`on-issues` and `on-pull-requests` options.  The default behavior is to run for both
issues and pull requests.

You can also toggle automatically locking the conversation and closing the issue or
pull request using the `lock` and `close` options respectively.  The default
behavior is to both lock and close.

Note that a token with write permissions for issues and/or pull requests is required
(as necessary).

```yaml
name: Let fate decide

on:
  issues:
    types: [opened, reopened]
  pull_request:
    types: [opened]

jobs:
  notify:
    runs-on: ubuntu-latest
    permissions:
      issues: write
      pull-requests: write
    steps:
      - uses: FastAndCheap/maybe-not@v1
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          fail-percentage: 5
          on-issues: true
          on-pull-requests: true
          lock: true
          close: true
```
