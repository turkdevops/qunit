---
layout: page-api
title: assert.step()
excerpt: A marker for progress in a given test.
groups:
  - assert
version_added: "2.2.0"
---

`step( message )`

A marker for progress in a given test.

| name | description |
|------|-------------|
| `message` (string) | Message to display for the step |

The `step()` assertion registers a passing assertion with a provided message. This makes it easy to check that specific portions of code are being executed, especially in asynchronous test cases and when used with `verifySteps()`. A step will always pass unless a message is not provided or is a non-string value.

Together with the [`assert.verifySteps`](./verifySteps.md) method, `step()` assertions give you an easy way to verify both the count and order of code execution.

## Examples

```js
QUnit.test( "step example", assert => {
  const thing = new MyThing();
  thing.on( "something", () => {
    assert.step( "something happened" );
  });
  thing.run();

  assert.verifySteps([ "something happened" ]);
});
```

_Note: See [`assert.verifySteps()`](./verifySteps.md) for more detailed examples._
