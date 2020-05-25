# robotframework-gui-rest

Intended to run in CI pipelines (GitLab, Jenkins,...). Based on ppodgorsek/docker-robot-framework:
- RESTinstance library added,
- tests auto-executing feature disabled (run-tests-in-virtual-screen.sh is not fired after loading image).
YAML file GitLab example
variables:
  BROWSER_MODE: 'Headless_Chrome'
  ENV_URL_APP: '<application URL>'
  ENV_URL_API: '<API base URL>'
  ROBOT_TESTS_DIR: "$CI_PROJECT_DIR/tests" *)
  ROBOT_REPORTS_DIR: "$CI_PROJECT_DIR/reports"
script
  robot -v ENV_URL_APP:$ENV_URL_APP -v ENV_URL_API:$ENV_URL_API -v BROWSER_MODE:$BROWSER_MODE --escape space:_ --outputDir $ROBOT_REPORTS_DIR $ROBOT_TESTS_DIR

*) $CI_PROJECT_DIR is on of predefined GitLab environment variables.
