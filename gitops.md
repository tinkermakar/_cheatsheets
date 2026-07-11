# CI/CD Cheatsheet

1. In GitHub Actions, use composite actions to reuse individual steps and reusable workflows (`workflow_call`) to reuse whole jobs or groups of jobs.

1. Keep workflow triggers separate from implementation:
    1. regular workflows define when a pipeline runs
    1. reusable workflows contain the actual jobs, commands, and marketplace actions

    Example source tree for a monorepo with several services:
    ```text
    .github/
    ├── composite-actions/
    │   ├── cache/action.yml          # reusable group of steps
    │   └── prepare-cloud/action.yml  # another composite action
    └── workflows/
        ├── _install.yml              # reusable workflow: workflow_call
        ├── _lint.yml                 # reusable workflow: workflow_call
        ├── _test.yml                 # reusable workflow: workflow_call
        ├── _deploy.yml               # reusable workflow: workflow_call
        ├── service-a.yml             # push/PR triggers and orchestration
        ├── service-b.yml             # push/PR triggers and orchestration
        └── manual-deploy.yml         # workflow_dispatch trigger
    ```

    A trigger workflow calls the implementation and passes its inputs and secrets:
    ```yaml
    jobs:
      deploy:
        uses: ./.github/workflows/_deploy.yml
        with:
          target-environment: ${{ github.ref_name }}
          working-directory: services/service-a
        secrets: inherit
    ```

1. Put pipeline logic in reusable workflows even when it has only one caller. This makes it easier to move shared CI/CD logic into a central repository later.
