# Github Action to sync a public branch to a private repo

![001](https://github.com/stavares843/sync-public-branch/assets/29093946/2248f93c-061e-40f7-a240-df9b6a04a73c)

# Description

If you have a public repo and want to test something with the same content on a private repo and you need a specific branch, you can do a private repo by
- Create a new repo
- Import the repo using the public URL
- You now have a private repo with the same content as the public one, but it's not synced automatically
- Add the above file as a workflow and update it with the correct repo info
- Go to actions, select the action, click on run workflow, add the branch name from the public repo you want to send over to the private one, and run the action
- When you add a new commit on the public repo, re-running the action will update the branch on the private repo with the latest commit as well

# Usage

https://github.com/stavares843/sync-public-branch/assets/29093946/23ddeb22-f7f0-4288-ae02-ce77718e798a


<p align="center">
   <a href="/LICENSE"><img src="https://img.shields.io/badge/license-MIT-green.svg?style=flat" /></a>
</p>

# Notes

If your repo has a `.workflows` folder you need to add the following to avoid this error

<img width="713" alt="Captura de ecrã 2024-02-13, às 16 37 54" src="https://github.com/stavares843/sync-public-repo-to-private-repo/assets/29093946/feeafdd8-f216-486f-b65f-4e534bd8507a">

- You need to create a token with `contents:write` and `workflows:write` scopes and add it on the checkout step

```
      - name: Check out code
        uses: actions/checkout@v4
        with:
          # Fine-grained PAT with contents:write and workflows:write scopes
          token: ${{ secrets.WORKFLOW }}
``` 
