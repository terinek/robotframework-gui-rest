# robotframework-gui-rest

Intended to run in CI pipelines (GitLab, Jenkins,...). Based on ppodgorsek/docker-robot-framework:
- RESTinstance library added,
- tests auto-execution feature disabled (run-tests-in-virtual-screen.sh is not fired after loading image).

YAML GitLab file example (gitlab-ci.yml):
``` yaml
image: "terinek007/robotframework-gui-rest:latest"

stages:
  - test

gui_test:
  stage: test
    variables:
      BROWSER_MODE: 'Headless_Chrome'
      ENV_URL_APP: '<application URL>'
      ENV_URL_API: '<API base URL>'
      ROBOT_TESTS_DIR: "$CI_PROJECT_DIR/tests"
      ROBOT_REPORTS_DIR: "$CI_PROJECT_DIR/reports"
  script:
  - robot -v ENV_URL_APP:$ENV_URL_APP -v ENV_URL_API:$ENV_URL_API -v BROWSER_MODE:$BROWSER_MODE --escape space:_ --outputDir $ROBOT_REPORTS_DIR $ROBOT_TESTS_DIR
```
Note: $CI_PROJECT_DIR is one of predefined [GitLab environment variables](https://docs.gitlab.com/ee/ci/variables/predefined_variables.html).
