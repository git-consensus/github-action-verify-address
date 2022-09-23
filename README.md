# github-action-verify-address

This action checks if a PR commit message contains a ethereum wallet address.

## Create Workflow

Create a workflow like the one below (also in example directory):
```yaml
      - name: Checkout
        uses: actions/checkout@v2
      - name: Commit Address Check
        id: Testing
        uses: git-consensus/github-action-verify-address@v1.0
```

NOTE:
The PR commit message wallet address must be seperated by a separator input (default: space) from the message.
Example:
initial commit 0x0... (O)

github commit 0x0... message (O)

commit message0x0... (X)

We are able to change the separator with this as an option:

## Custom Separator (Example)
```yaml
    with:
    separator: "\n"
```

## Invoking the action only when the pull request is merging (Example):
```yaml
on:
  pull_request_target:
    types:
      - closed

jobs:
  if_merged:
    if: github.event.pull_request.merged == true
    runs-on: ubuntu-latest
    name: Commit Message Print
    steps:
      - name: Checkout
        uses: actions/checkout@v2
      - name: Commit Addres Check
        id: Testing
        uses: git-consensus/github-action-verify-address@v1.2
#        uses: aagusuab/wallet-commit-check-action@v9.3
        with:
          separator: " "


```
