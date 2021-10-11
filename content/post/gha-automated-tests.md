+++
title = "Run Flutter Integration Tests in GitHub Actions"
date = "2021-10-11"
author = "Zachary Russell"
description = "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam nec interdum metus. Aenean rutrum ligula sodales ex auctor, sed tempus dui mollis. Curabitur ipsum dui, aliquet nec commodo at, tristique eget ante."
+++

One of Flutter's greatest strengths is being able to abstract coding applications for multiple platforms. One of the most useful features that Flutter has within this toolset is the ability to run visual integration tests against multiple platforms.

GitHub has built-in CI/CD through [GitHub Actions](https://github.com/features/actions) which allows you to run integration tests automatically with ease.

In this article we'll explore using Flutter for Web integration tests.

### Why Test Using Flutter for Web

This is not ideal in all scenarios, meaning your app will need to support Flutter for Web in order for this to work. You _can_ run Flutter integration tests in iOS and Android using GitHub Actions, however it requires you use a MacOS runner which costs 10x what a Linux runner does. For real production apps it is definitely recommended to use the target platform to run tests. In a future article I will explore using both MacOS runners and Firebase Test lab for integration tests.

## Create a new Flutter Project

(note: for the first steps of this project you can follow the [official integration testing docs](https://flutter.dev/docs/cookbook/testing/integration/introduction))

To begin, lets make a new project to house our tests:

`flutter new test_project`

Then go into the project's folder and type `flutter run` to get your project up and running.

## Install the `integration_test` Package

## Write Tests

## Run Integration Tests Locally

## Set up GitHub Actions to run Integration Tests

In order to create a GitHub Action you must create a file with the `.github/workflows` directory. In this case we'll call it `integration-tests.yml`

```yaml
name: Flutter Integration Tests
on: [push, pull_request]
jobs:
  integration_tests:
    runs-on: ubuntu-20.04
    steps:
      - uses: actions/checkout@v2
      - uses: subosito/flutter-action@v1
      - run: flutter pub get
      - run: chromedriver --port=4444 &
      - run: flutter drive --driver=test_driver/integration_test.dart --target=integration_test/app_test.dart -d web-server
```
