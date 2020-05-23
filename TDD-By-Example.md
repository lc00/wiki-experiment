## Patterns For Test-Driven Development

* Tests are about keeping stress down
  * You won't test-last, because you'll be running out of time, which increases stress, which decreases the likelihood you'll test.
* Tests shouldn't depend on each other
* Use only enough data to communicate clearly
* Make the source of the data evident- no guessing about why you picked some number
* When you're programming alone, leave the last test started but failing. This will help you get in the mindset when you come back. When programming in groups, always check the code in clean.
* Fixtures can be powerful, but they can also make the tests harder to read
* You should test conditionals, loops, operations, and polymorphism
* Bad design smells: Long setup code, setup duplication, long-running tests, fragile tests
* Decide how many tests to write based on how long you want your "mean time between failures" to be. If it's critical, test more corner-cases. If they're rare, leave them.
* Delete tests if doing so doesn't decrease confidence or clarity
* If you're totally lost, throw it away and start over again.
* Don't be distracted by new ideas, just add them to your test list and stay focused.

### Sequence

1. Start by listing out the tests you'll need to write
1. Pick a test that will teach you something and that you are confident you can implement
  * **Child Tests**: If making a big test pass is too much, write a smaller test that represents the bigger broken part, make it pass, reintroduce the bigger test.
1. Choosing a test type:
  * **Starter tests**:
    * Test a variant of an operation that doesn't do anything
      * This answers the question "where does it belong?", and only that
    * Test for the output being the same as the input
    * Test for the smallest input possible (empty or 1)
  * **Example tests**: Come up with an example of how something should work by way of a test
  * **Learning Tests**: Test the parts of external software you're using, to learn how and verify they work
  * **Regression Tests**: Write the smallest test that verifies the bug. Refactor the system so this is possible, if necessary.
1. Write the assert statements first
1. Write the setup and action code:
  * **Mock Objects**: Make pretend versions of things like databases and networks. Mock objects improve readability and communication. Test your mock objects by using the same tests for them and for the real thing.
  * **Self-Shunt**: Use the test case itself as way to communicate with the object under test, store variables, etc.
  * **Log String**: Put logged messages in a string, and then test the value of the string.
  * **Crash Test Dummy**: Make a version of an object that just throws an exception when an overridden method is called.
1. Starting building the implementation. Some strategies:
  * Return a constant. This duplicates the test code, so you keep refactoring until it doesn't.
  * Triangulate. Come up with enough examples that you gradually get to the implementation- only use this if you're really unsure about what the abstraction should look like
  * Obvious implementation. If you feel like you know what it should be, just write it. Be prepared to delete and "downshift" if you start getting surprised.
  * With collections, get it working with one item in the collection first.

### Refactoring

* Gradually make things identical, then delete the duplicate
* Isolate change by extracting methods
  * Bodies of loops, whole loops, branches of conditionals
  * Helps understand complicated code
* Migrate data by temporarily duplicating it
* Inline methods by copy/pasting the implementation over the invocation

### Breaks

Not taking breaks impedes your judgment, which increases fatigue, which impedes judgment.

* Keep a water bottle at your desk to make sure bathroom breaks interrupt you
* Make after-hours commitments so that you have to stop programming
* Have weekend commitments to keep your mind off work
* Take a month off a year
