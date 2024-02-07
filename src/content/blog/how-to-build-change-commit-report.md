---
author: Eka Prasetia
pubDatetime: 2023-05-10T13:00:00.700+07:00
title: How to build change commit report with AI
slug: change-commit-report-with-ai
featured: false
tags:
  - ai
description: 🤖 Generates a report from the recent code commit changes and posts it to Slack.
---

This is simple [demo code](https://github.com/ekaone/change-commit-report) to generate a report from the recent code commit changes and post it to Slack. The code is written in Typescript and uses OpenAI's GPT-3 to generate the report.

This action generates a report from the recent code commit changes and posts it to Slack.

```yaml
name: "Run"
on:
  workflow_dispatch:
  schedule:
    - cron: "0 10 * * 1" # Run every Monday at 10am UTC

jobs:
  run: # make sure the action works on a clean machine without building
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
        with:
          fetch-depth: 250 # Use a large enough fetch depth to ensure the action can find the commit history to work with

      - uses: ekaone/change-commit-report@main
        with:
          days: 7 # Number of days to include into the report
          channel: "general" # Slack channel to post the report to
        env:
          OPENAI_API_KEY: ${{ secrets.OPENAI_API_KEY }} # Your OpenAI API key, used to generate the report
          SLACK_BOT_TOKEN: ${{ secrets.SLACK_BOT_TOKEN }} # Your Slack bot token, used to post the report on behalf of the bot
          SLACK_SIGNING_SECRET: ${{ secrets.SLACK_SIGNING_SECRET }} # Your Slack signing secret, used to verify the request is coming from Slack
```

Let me explain each part of the code:

This code is a [GitHub Actions workflow](https://docs.github.com/en/actions/using-workflows) file that defines a set of automated tasks to run on certain events or schedules. Let me explain each part of the code:

- `name: "Run"` sets the name of the workflow. This name will be displayed on the repository's "Actions" tab.
- `on:` specifies the events that trigger the workflow. In this case, the workflow can be triggered manually by using the `workflow_dispatch` event, or automatically by using the `schedule` event. The `schedule` event uses a `cron` expression to define the frequency of the workflow. In this case, the workflow will run every Monday at 10am UTC.
- `jobs:` defines the actions that the workflow performs. Each job has a unique identifier, such as `run` in this case, and runs on a specific runner machine, such as `ubuntu-latest` in this case. Each job consists of one or more steps, which are the individual tasks that the job executes.
- `- uses: actions/checkout@v3` is a step that uses a predefined action from the GitHub Actions marketplace. This action checks out the repository code on the runner machine, so that it can be used by subsequent steps. The `@v3` indicates the version of the action to use. The `with:` keyword specifies the input parameters for the action. In this case, the `fetch-depth` parameter is set to 250, which means that the action will fetch the last 250 commits from the repository history. This is useful for actions that need to access the commit history, such as the next step.
- `- uses: ekaone/change-commit-report@main` is another step that uses a custom action from the GitHub Actions marketplace. This action generates a report of the changes and commits made to the repository in the last specified number of days, and posts it to a Slack channel. The `@main` indicates the branch of the action repository to use. The `with:` keyword specifies the input parameters for the action. In this case, the `days` parameter is set to 7, which means that the report will cover the last 7 days of activity. The `channel` parameter is set to "general", which means that the report will be posted to the general channel on Slack. The `env:` keyword specifies the environment variables for the action. In this case, the action needs three environment variables: `OPENAI_API_KEY`, `SLACK_BOT_TOKEN`, and `SLACK_SIGNING_SECRET`. These [variables](https://docs.github.com/en/actions/learn-github-actions/variables) are stored as secrets in the repository settings, and can be accessed by using the syntax `${{ secrets.VARIABLE_NAME }}`. This way, the action can use the OpenAI API key to generate the report, the Slack bot token to post the report on behalf of the bot, and the Slack signing secret to verify the request is coming from Slack.

Thank you for reading this article, I hope you find it useful. Grab the code from [here](https://github.com/ekaone/change-commit-report), happy coding! 😃
