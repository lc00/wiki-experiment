## The Testing Pyramid

* UI tests are powerful, but slow and brittle, and speed matters
* Levels of testing apply to levels of architecture:
    * UI - UI. Use sparingly.
    * Integration - Service. Cover unit test gaps.
    * Unit Tests - Logic. Favor over UI tests.
* Unit tests are what enable you to iterate quickly

## Smoking User Interface Tests

* Smoke test- Are our applications correctly deployed, environments correctly configured, and pieces of our architecture hooked up correctly?
* Use variables for commonly used URLs
* Record/playback UI tests are brittle and unreadable

## Adding UI Tests to Legacy Systems

Steps: 

1. Confirm you're on the right page
2. Find the right selectors (prefer IDs)
3. Make assertions

* The tighter you couple the test to your interface details, the more brittle it is.
* Use `before` blocks for clean up and setup

## Connecting the Dots with Integration Tests

## Integration Testing RESTful Web Services

## Covering Our Bases with Unit Tests

## Unit Testing in the Browser with JavaScript

## Climbing the Pyramid

## Programming 101

## Organizing Tests

## Effective Mocking

## Writing Tests First

