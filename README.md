# GITHUB ACTIONS
* For CI/CD pipelines
* Simple Workflows

## TASKS
* CI
* CD and Delivery
* Terraform cloud and IaC
* GitOps with ArgoCD and Flux
* Using and scaling self hosted runners
* AppSec with GitHub Advanced Security
* Not only for CI/CD but also for automation


## SYNTAX
* `Events` - everything stats with `events` (`pull`, `push` to a `branch`, `issues` (open, close, reopen))
* `Events` trigger `workflows`
* `Workflows` have atleast one `job`
* Each `job` has at least one `step` (action/shell command)
* Each `job` is associated with a `runner` which runs independently
* `Runner` is a `machine` that is connected with github
* Each `step` is `logged` and logs are saved
* Each `step` in a job is run `sequentially`
* Each `job` can run `independently` and `parallely`
* `Runners` are of two type - (`self hosted`, `github runners`(ubuntu, max, windows))



## CREATING A ACTION
* Create a directory `.github` in the cloned repo
* Create a directory `.github/workflows` in the cloned repo
* change directory to `.github/workflows`
* Example :
```yaml
name: <workflow_name>
on:
  push: # an event
    branches: # define which branch this workflow will be triggered upon
      - main
  pull_request: # an event
    branches: # define which branch this workflow will be triggered upon
      - main
  workflow_dispatch: # helps to trigger an event without pushing changes to repo

jobs:
  hello: # job name
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2 # define the action that will be used to do all the tasks (<github_repo>@<release_version/tag/commit_hash/branch_name>)
      - name: hello world # step name
        run: echo "Hello World" # run shell command
        shell: bash # specify the shell that will be used

  goodbye:
    runs-on: ubuntu-latest
    steps:
      - name: goodbye world
        run: echo "Goodbye World"
        shell: bash
```
