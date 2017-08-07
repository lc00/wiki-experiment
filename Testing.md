## Categories of Tests

* Unit - Fast, low-level tests that target a small part of the system. A unit is a small chunk of functionality (function, class, small cluster) that can be tested in a meaningful way.
* Integration - Not a unit, not a system.
* System - Test the entire integrated system or component, black box.
* Acceptance - Automated test for a story

## Types of tests

* Functional - Does the software do what it was intended to do? Does it not do what it was not intended to do?
* Nonfunctional
    * Performance testing - how quickly?
    * Load testing - With the system under normal use
    * Stress testing - With the system under extreme load
    * Spike testing - With the system under immediate extreme load
    * Security testing - Validation/Audit of policy, or blackhat penetration test
    * Confidentiality
        * Private information stays that way
        * User control over what information is stored
    * Integrity
        * Data can only be changed by trusted sources
        * System can perform without being compromised
    * Availability - Resources are available to authorized users and denied to others
    * Common hit list
        * Avoid sending data over networks
        * Protect against people using common sets of credentials
        * SQL injection
    * Regression testing - How do we know we haven’t broken anything?
    * Smoke tests - Can it do something basic, like log in?
    * Characterization testing - Adding tests to a legacy app
    * Positive testing - The happy path
    * Negative testing - Invalid values

## Testing strategy

Which tests are part of the definition of done, which get run once an iteration, which ones are only on delivery, etc. Some require specific skillsets. Some can be strategically ignored.

## Agile Testing Quadrants
Business-facing vs. technology-facing
Guide development vs. critique the product

![Agile Testing Quadrants](https://s3-us-west-2.amazonaws.com/kylecoberly-projects/images/agile-testing-quadrants.jpeg)

## Testability
A program element can be put in a known state, acted on, and then observed. Observing direct output can be difficult, because adding logs and “observation points” in a method can affect its implementation. In OOP, that may mean relaxing visibility (private to package-scoped), or just test the public API.
