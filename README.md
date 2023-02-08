# Unit-1-01
---

#################################

#################################

## Super Linter GitHub Actions ##

#################################

#################################

name: Lint Code Base



#

# Documentation:

# https://docs.github.com/en/actions/learn-github-actions/workflow-syntax-for-github-actions

#



#############################

# Start the job on all push #

#############################

on:

  push:

  pull_request:

    branches: [master, main]



###############

# Set the Job #

###############

jobs:

  build:

    # Name the Job

    name: Lint Code Base

    # Set the agent to run on

    runs-on: ubuntu-latest



    ##################

    # Load all steps #

    ##################

    steps:

      ##########################

      # Checkout the code base #

      ##########################

      - name: Checkout Code

        uses: actions/checkout@v3

        with:

          # Full git history is needed to get a proper list of changed files within `super-linter`

          fetch-depth: 0



      ################################

      # Run Linter against code base #

      ################################

      - name: Lint Code Base

        uses: github/super-linter@v4

        env:

          VALIDATE_ALL_CODEBASE: false

          DEFAULT_BRANCH: master

          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
