# GitHub Actions Lab: Workflow vs Job vs Step

## Objective
In this lab, I learned the difference between **workflow**, **job**, and **step** in GitHub Actions. I observed how jobs run in parallel and steps run sequentially within each job. Additionally, I modified the workflow to add a job dependency, ensuring that **job-two runs after job-one** using the `needs` keyword.

## Setup
The workflow file is located in the `.github/workflows/` directory. The file name is `lab-actions.yml`.

## Final Workflow (with dependency)
```yaml
name: Workflow vs Job vs Step Lab

on: push

jobs:
  job-one:
    runs-on: ubuntu-latest
    steps:
      - name: Step 1 - Print message
        run: echo "This is Step 1 in Job One"
      - name: Step 2 - Print another message
        run: echo "This is Step 2 in Job One"

  job-two:
    needs: job-one
    runs-on: ubuntu-latest
    steps:
      - name: Step 1 - Print message
        run: echo "Job Two runs after Job One"
