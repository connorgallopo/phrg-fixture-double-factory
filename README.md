# Fixture vs Double vs Factory

## Fixtures

Developers often use fixtures when their tests rely on static data. If a developer notices that their tests keep needing the exact same information, they may construct a fixture to DRY up their tests.

## Doubles

Using test doubles is appropriate when there is functionality in an example that needs to respond a certain way, but is not the actual functionality that the example aims to test. While this may be a response from an outside API, it could also be an object in the application’s domain itself.

Let’s say an example aims to assert that an instance of `A` behaves a certain way, but as a byproduct, it checks an instance of `B` returns a certain value. Our example does not care about all the functionality of `B`, it just needs to simulate a line called against an instance of `B` returns that value. In this case, using a double instead of factory may create a simpler and faster test example. If there is not a need to create a full fledged instance of `B`, then do not do so. Use a double instead.

## Factories

Sometimes making an assertion in an example requires the creation of one or more models in your domain. If an example asserts that a particular model always behaves a certain way, then the only way to guarantee that is to use an instance that model. A double would jeopardize the intent of the test.

In this case, factories are the way to go.
