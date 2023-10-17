---
title: "If you want your .env.{stage} deployed to lambda"

categories:
  - Notes
tags:
  - [serverless]

permalink: /categories/notes/2

toc: true
toc_sticky: true

date: 2023-10-17
last_modified_at: 2023-10-17
---

If you do not specify your environment variables in the serverless.yaml file, they will not be deployed to your Lambda function. I haven't known it because it worked on local without any problems.. 
```yaml


service: user-consent
frameworkVersion: '3'

useDotenv: true

provider:
  name: aws
  region: ap-southeast-1
  environment:
    VARIABLE: ${env:VARIABLE}

  ...


```

If you don't want this injection codes, just use serverless-dotenv-plugin, I don't recommend it.




