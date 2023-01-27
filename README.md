
<p align="center">
  <img witdh="150px" height="150px" alt="clobbr grid logo" src="https://user-images.githubusercontent.com/1515742/80861783-dcfcc400-8c70-11ea-89c6-671dbdff6f33.png" />
  <h3 align="center">
    Clobbr CI integration examples <br/>
    <small><a href="https://clobbr.app">clobbr.app</a></small> <br/>
    <a href="https://www.npmjs.com/package/@clobbr/cli" target="_blank">
      <img src="https://img.shields.io/npm/v/@clobbr/cli?label=npm&style=flat" alt="get @clobbr/cli on npm">
    </a>
  </h3>
</p>

This repository contains examples on how to integrate [@clobbr/cli](https://github.com/parsecph/clobbr/tree/master/packages/cli) in various CIs.

In the CI of choice, make sure nodejs is available (recommended version: 14.x) and run checks with clobbr cli, for example:

```bash
npx @clobbr/cli run \
  --url "https://api.github.com/zen" \
  --checks mean=200 median=200 stdDev=50 q5=150 q50=200 q95=250 q99=300 pctOfSuccess=95
```

<img width="450px" alt="Run checks against results" src="https://user-images.githubusercontent.com/1515742/189538796-4d96f78f-0251-41e4-a549-bcb04eab2fb2.png">

If any of the checks fail, the CI will fail.

[Go to main documentation to see more ↗️](https://github.com/parsecph/clobbr/blob/master/README.md)

### Tested CIs
#### CI usage examples

<a href="https://app.circleci.com/pipelines/github/parsecph/clobbr-ci/471/workflows/706bab66-3ced-4a60-aca1-f832e1d1e85a/jobs/470/parallel-runs/0/steps/0-102">
  <img width="200px" alt="CircleCI integration config" src="https://user-images.githubusercontent.com/1515742/189537171-4a064b0d-3db9-4016-9baf-f6b6ac49f45d.png">
</a>

<a href="https://app.travis-ci.com/github/parsecph/clobbr-ci">
  <img width="200px" alt="Travis CI integration config" src="https://user-images.githubusercontent.com/1515742/189537172-c4e01aaf-16f2-499f-92d5-924c82a44540.png">
</a>

<a href="https://ci.appveyor.com/project/dandaniel/clobbr-ci">
  <img width="200px" alt="AppVeyor CI integration config" src="https://user-images.githubusercontent.com/1515742/189537169-1b6b812a-9830-4573-955d-b25ccec27e08.png">
</a>

##### circleci

```yaml
version: 2.1

orbs:
  node: circleci/node@4.7

jobs:
  build:
    working_directory: ~/repo
    docker:
      - image: circleci/node:16.7.0
    steps:
      - checkout
      - run:
          name: Run clobbr
          command: npx @clobbr/cli run -u "https://60698fbde1c2a10017544a73.mockapi.io" --checks mean=200 median=200 stdDev=50 q5=150 q50=200 q95=250 q99=300 pctOfSuccess=95

```

##### travis

```yaml
language: node_js
node_js:
  - "16"
script: npx @clobbr/cli run -u "https://60698fbde1c2a10017544a73.mockapi.io" --checks mean=200 median=200 stdDev=50 q5=150 q50=200 q95=250 q99=300 pctOfSuccess=95
```

##### appveyor

```yaml
image: Ubuntu

environment:
  nodejs_version: "16"

test_script:
  - node --version
  - npm --version
  - npx @clobbr/cli run -u "https://60698fbde1c2a10017544a73.mockapi.io" --checks mean=200 median=200 stdDev=50 q5=150 q50=200 q95=250 q99=300 pctOfSuccess=95

build: off
```

-----------------

<a href="https://apihustle.com" target="_blank">
  <img height="60px" src="https://user-images.githubusercontent.com/1515742/215217833-c07183d2-f688-4d1c-86ea-329f3b28f81c.svg" alt="Apihustle Logo" />
</a>

This tool is part of the Apihustle suite - a collection of tools to test, improve and get to know your API inside and out. <br/>
[apihustle.com](https://apihustle.com) <br/>

|    |    |    |    |
| :- | :- | :- | :- |
| <a href="https://clobbr.app" target="_blank"><img height="70px" src="https://user-images.githubusercontent.com/1515742/215217949-0fe7096c-10f1-47ec-bdc7-91d8047ddc70.svg" alt="Clobbr Logo" /></a> | **Clobbr** | Debug multiple cron expressions on a calendar. | [clobbr.app](https://clobbr.app) | 
| <a href="https://crontap.com" target="_blank"><img height="70px" src="https://user-images.githubusercontent.com/1515742/215218037-44233c7d-7e21-4180-8572-6a759a6a118f.svg" alt="Crontap Logo" /></a> | **Crontap** | Schedule API calls using cron syntax. | [crontap.com](https://crontap.com) | 
| <a href="https://tool.crontap.com" target="_blank"><img height="70px" src="https://user-images.githubusercontent.com/1515742/215217997-fedcc496-a868-40bd-81f9-d07dabc0597e.svg" alt="CronTool Logo" /></a> | **CronTool** | Debug multiple cron expressions on a calendar. | [tool.crontap.com](https://tool.crontap.com)  |

-----------------

![Clobbr icon](https://user-images.githubusercontent.com/1515742/80861773-da9a6a00-8c70-11ea-9671-77e1bb2dea04.png)
