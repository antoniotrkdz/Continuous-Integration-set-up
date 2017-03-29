# Continuous-Integration-set-up
Small How-To on setting up CI with Travis and Codecov

1. Make sure you set up the testing in your node setup (package.json)
```json
"devDependencies": {
    "istanbul": "^0.4.5",
    "nodemon": "^1.11.0",
    "pg": "^6.1.5",
    "shot": "^3.4.0",
    "tap-spec": "^4.1.1",
    "tape": "^4.6.3"
  }
```
1. Sign up (if you haven't already) to [travis-ci](https://travis-ci.org) using GitHub account and sync.
1. Enable the repo you want to be Continuously Integrated.
1. Make a .travis.yml file:
```yaml
  language: node_js
  node_js:
  - '7'

  script:
    npm run coverage

  before_install:
    - pip install --user codecov
  after_success:
    - codecov --file coverage/lcov.info --disable search

  notifications:
    email:
      on_success: never
      on_failure: never
```
1. Go to [Codecov](https://codecov.io) and sign up (if you haven't already).
1. Chose your repo to integrate from the menus or add a new one.
(make not e of the token for your reference)
1. Add the badges to the README.md file of your repo
```md
[![Travis-Badge-Build](https://api.travis-ci.org/your-repo.svg](https://travis-ci.org/your-repo)
[![Code Coverage](https://codecov.io/gh/your-repo.svg)](https://codecov.io/gh/your-repo)
```
