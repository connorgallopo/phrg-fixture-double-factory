# Fixture vs Double vs Factory

## Fixtures

Developers often use fixtures when their tests rely on static data. If a developer notices that their tests keep needing the exact same information, they may construct a fixture to DRY up their tests. Fixtures may be located in the spec file itself, in a test support file, or even directly in a factory definition.

## Doubles

Using test doubles is appropriate when there is functionality that needs to respond a certain way, but is not the actual process that an example aims to test. While this may be for return value from an external API, it could also just be an object in the application’s domain itself.

Let’s say an example aims to assert that an instance of `A` behaves a certain way, but as a byproduct, it checks that an instance of `B` returns a distinct value. Our example does not care about all the functionality of `B`, it just needs to simulate that when a line is called against an instance of `B`, it returns that distinct value. In this case, using a double instead of factory may create a simpler and faster test example.

If there is no need to create a full fledged instance an object, then do not do so. Use a double instead.

## Factories

Sometimes making an assertion in an example requires the creation of one or more models in your domain. If an example asserts that a particular model **always** behaves a certain way, then the only way to guarantee this is to use an actual instance of the model. Using a double would jeopardize the intent of the test.

In this case, factories are the way to go. A factory sets up an actual model in our domain.
