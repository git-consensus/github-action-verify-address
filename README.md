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
The PR commit message wallet address must be seperated by a space " " character from the message.
Example:
initial commit 0x0... (O)

github commit 0x0... message (O)

commit message0x0... (X)


