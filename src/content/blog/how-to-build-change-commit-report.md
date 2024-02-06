---
author: Eka Prasetia
pubDatetime: 2023-05-10T13:00:00.700+07:00
title: How to build change commit report with AI
slug: change-commit-report-with-ai
featured: false
ogImage: https://user-images.githubusercontent.com/53733092/215771435-25408246-2309-4f8b-a781-1f3d93bdf0ec.png
tags:
  - ai
description: 🤖 OpenAI - Generates a report from the recent code commit changes and posts it to Slack.
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
