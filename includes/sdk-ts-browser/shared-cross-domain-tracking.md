You can track anonymous behavior across two different domains. Amplitude identifies anonymous users by their device IDs which must be passed between the domains. To maintain the same session and ensure a continuous user journey, also pass session IDs to the other domain. 

!!! note

    Starting from `v2.8.0` the SDK supports getting the device ID from the URL paramter `ampDeviceId`. The SDK configuration, for example, `init('API_KEY', { deviceId: 'custom-device-id' })` still takes precedence over the URL parameter. Previous versions of the SDK supported the `deviceId` URL parameter, this option is still supported for backward compatibility but `ampDeviceId` will take precedence if both are set. You don't need to change your code if upgrade to versions higher than `v2.8.0` but it is recommended.

For example:

* Site 1: `www.example.com`
* Site 2: `www.example.org`

Users who start on Site 1 and then navigate to Site 2 must have the device ID generated from Site 1 passed as a parameter to Site 2. Site 2 then needs to initialize the SDK with the device ID.
 The SDK can parse the URL parameter automatically if `deviceId` is in the URL query parameters.

Starting from `v2.8.0`, the SDK can automatically get session ID from the URL to maintain the same session and ensure a continuous user journey.

1. From Site 1, grab the device ID from `getDeviceId()` and the session ID from `getSessionId()`.
2. Pass the device ID and session ID to Site 2 via a URL parameter when the user navigates. (for example: `www.example.com?ampDeviceId=device_id_from_site_1&ampSessionId=1716245958483`)
3. Initialize the Amplitude SDK on Site 2 with `init('API_KEY', null)`.

If the `deviceId` and `sessionId` aren't set in `init('API_KEY', null, { deviceId: 'custom-device-id', sessionId: 1716245958483 })`, the SDK automatically falls back to using the URL parameters respectively.

It's recommended to follow the same session ID format as the Browser SDK by using `Date.now()`. Because the SDK checks whether an event is in session every time an event is tracked. For example, 

```typescript
// if session ID is set to 12345
// https://www.example.com?ampDeviceId=my-device-id&ampSessionId=12345
amplitude.init(API_KEY)
// session ID is set to 12345 after init()

amplitude.track("event")
// session ID is set back to Date.now() 
// because the tracked "event" is not in the previous session 12345
```
