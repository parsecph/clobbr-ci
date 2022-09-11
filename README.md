
<p align="center">
  <img witdh="150px" height="150px" alt="clobbr grid logo" src="https://user-images.githubusercontent.com/1515742/80861783-dcfcc400-8c70-11ea-89c6-671dbdff6f33.png" />
  <h2 align="center">Clobbr CI integration examples</h2>
</p>

This repository contains examples on how to integrate [@clobbr/cli](https://github.com/parsecph/clobbr/tree/master/packages/cli) in various CIs.

In the CI of choice, make sure nodejs is available (recommended version: 14.x) and run checks with clobbr cli, for example:

```bash
npx @clobbr/cli run -u "https://example.com/api" --checks mean=200 median=200 stdDev=200 q5=200 q50=200 q95=200 q99=200 pctOfSuccess=95
```

If any of the checks fail, the CI will fail.

[Go to main documentation to see more ↗️](https://github.com/parsecph/clobbr/blob/master/README.md)

### Tested CIs
#### CI usage examples

<a href="https://github.com/parsecph/clobbr-ci/blob/main/.circleci/config.yml">
  <img width="200px" alt="CircleCI integration config" src="https://user-images.githubusercontent.com/1515742/189537171-4a064b0d-3db9-4016-9baf-f6b6ac49f45d.png">
</a>

<a href="https://github.com/parsecph/clobbr-ci/blob/main/.travis.yml">
  <img width="200px" alt="Travis CI integration config" src="https://user-images.githubusercontent.com/1515742/189537172-c4e01aaf-16f2-499f-92d5-924c82a44540.png">
</a>

<a href="https://github.com/parsecph/clobbr-ci/blob/main/appveyor.yml">
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
          command: npx @clobbr/cli run -u "https://60698fbde1c2a10017544a73.mockapi.io" --checks mean=200 median=200 stdDev=200 q5=200 q50=200 q95=200 q99=200 pctOfSuccess=95

```

##### travis

```yaml
language: node_js
node_js:
  - "16"
script: npx @clobbr/cli run -u "https://60698fbde1c2a10017544a73.mockapi.io" --checks mean=200 median=200 stdDev=200 q5=200 q50=200 q95=200 q99=200 pctOfSuccess=95
```

##### appveyor

```yaml
image: Ubuntu

environment:
  nodejs_version: "16"

test_script:
  - node --version
  - npm --version
  - npx @clobbr/cli run -u "https://60698fbde1c2a10017544a73.mockapi.io" --checks mean=200 median=200 stdDev=200 q5=200 q50=200 q95=200 q99=200 pctOfSuccess=95

build: off
```

![Clobbr icon](https://user-images.githubusercontent.com/1515742/80861773-da9a6a00-8c70-11ea-9671-77e1bb2dea04.png)
