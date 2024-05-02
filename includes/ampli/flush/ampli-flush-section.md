### Flush

The Ampli wrapper queues events and sends them on an interval based on the configuration.

Call `flush()` to immediately send any pending events.

The `flush()` method returns a promise that can be used to ensure all pending events have been sent before continuing.
This can be useful to call prior to application exit.

Ampli flushes events in the buffer automatically when `flushQueueSize` or `flushInterval` are reached.

Ampli sends events automatically without calling `flush()`, but using `flush()` is useful if you need to send events before the application exits.