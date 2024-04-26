---
title: Autocapture
---

Amplitude's Autocapture plugin extends the events and properties that Amplitude tracks by default, and enables Visual Tagger to enable you to define events based on elements on your site. For more information about Visual Tagger, see [Visual Tagger](https://help.amplitude.com/hc/en-us/articles/24094812669979-Visual-tag-editor).

--8<-- "includes/alpha-release.md"

## Installation

Autocapture requires the latest versions of the Amplitude Browser SDK (@{$ browser.sdk.version $}) and the Autocapture plugin (@{$ browser.plugin.autocapture.version $})

=== "Script Loader"
    ```html
    <script defer src="https://cdn.amplitude.com/libs/analytics-browser-@{$ browser.sdk.version $}-min.js.gz"></script>
    <script defer src="https://cdn.amplitude.com/libs/plugin-autocapture-browser-@{$ browser.plugin.autocapture.version $}-min.js.gz"></script>
    ```
=== "NPM"
    ```bash
    npm install @amplitude/analytics-browser
    npm install @amplitude/plugin-autocapture-browser@beta
    ```
=== "Yarn"
    ```bash
    yarn add @amplitude/analytics-browser
    yarn add @amplitude/plugin-autocapture-browser@beta
    ```

## Initialize the plugin

The Amplitude Browser SDK supports a [plugin architecture](/data/sdk-plugins/) that enables features like Autocapture. To enable the plugin, update your code with one of the following snippets, depending on your implementation. Both methods require that you define the Autocapture plugin, then call `add()` to enable it.

=== "Script Loader"
    ```html
    <script type="module">
      window.amplitude.init(AMPLITUDE_API_KEY)
      const autocapturePlugin = window.amplitudeAutocapturePlugin.plugin();
      window.amplitude.add(autocapturePlugin);
    </script>
    ```
=== "NPM / Yarn"
    ```js
    import * as amplitude from '@amplitude/analytics-browser';
    import { autocapturePlugin } from '@amplitude/plugin-autocapture-browser';

    amplitude.init(AMPLITUDE_API_KEY);
    amplitude.add(autocapturePlugin());
    ```

## Configuration

The Autocapture plugin adds four settings that help you configure what the plugin tracks.

| <div class="big-column">Setting</div>                   | Default                                                                                              | Description                                                                                        |
| -------------------------- | ---------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| `cssSelectorAllowlist`     | `['a','button','input','select','textarea','label','[data-amp-default-track]','.amp-default-track']` | String[]. Accepts one or more CSS selectors that define which elements on the page to track.         |
| `pageUrlAllowlist`         | undefined                                                                                            | `(string|RegExp)[]`. Defines the URL, URLs, or URL pattern on which Amplitude tracks default events |
| `shouldTrackEventResolver` | undefined                                                                                            | Function. Programatically determines if Amplitude should or shouldn't track an event.              |
| `dataAttributePrefix`      | `data-amp-track`                                                                                     | Allows the plugin to capture data attributes as an event property                                  |

```js
const plugin = autocapturePlugin({
  cssSelectorAllowlist: [
    '.amp-tracking',
    '[amp-tracking]'
  ],
  pageUrlAllowlist: [
    'https://amplitude.com',
    new RegExp('https://amplitude.com/blog/*')
  ],
});
```

By default, if you don't use these settings, Amplitude tracks the default selectors on all page on which you enable the plugin.

!!! info "Specifying CSS Selectors"
    When specify the CSS selectors to track, your selection overrides the default. To retain the default selectors import the `DEFAULT_CSS_SELECTOR_ALLOWLIST` and include it in your code.

    ```js
    import { DEFAULT_CSS_SELECTOR_ALLOWLIST } from '@amplitude/plugin-autocapture-browser';

    const selectors = [
      ...DEFAULT_CSS_SELECTOR_ALLOWLIST,
      '.class-of-a-thing-i-want-to-track',
    ];
    ```

## New events

When you enable the Autocapture plugin, Amplitude sends two events, from which you can create Dynamic Events with Visual Tagger:

- `[Amplitude] Element Clicked`
- `[Amplitude] Element Changed`

These two events capture properties that describe the corresponding element and other context about the user's browser:

<!-- vale off-->
- `[Amplitude] Element ID`
- `[Amplitude] Element Class`
- `[Amplitude] Element Tag`
- `[Amplitude] Element Text` (Collected for `[Amplitude] Element Clicked`, only) 
- `[Amplitude] Element Href` (Collected for `[Amplitude] Element Clicked`, only)
- `[Amplitude] Element Position Left`
- `[Amplitude] Element Position Top`
- `[Amplitude] Viewport Height`
- `[Amplitude] Viewport Width`
- `[Amplitude] Page URL`
- `[Amplitude] Page Title`
- `[Amplitude] Element Selector`
- `[Amplitude] Element Attributes`
- `[Amplitude] Element Aria Label`
- `[Amplitude] Element Parent Label`
<!-- vale on-->

## Disable Autocapture

To disable Autocapture, remove the plugin from any pages that implement it, and set `defaultTracking: false` in the Amplitude initialization on that page.

=== "Script Loader"
    Remove the following lines of code:

    ```html
    <!-- load Amplitude Autocapture plugin -->
    <script defer src="https://cdn.amplitude.com/libs/plugin-autocapture-browser-@{$ browser.plugin.autocapture.version $}-min.js.gz"></script>
    <!-- initialize Amplitude SDK and Autocapture plugin -->
    <script type="module">
      const autocapturePlugin = window.amplitudeAutocapturePlugin.plugin();
      window.amplitude.add(autocapturePlugin);
    </script>
    ```
=== "NPM / Yarn"
    Remove the plugin:

    ```bash
    // npm
    npm uninstall @amplitude/plugin-autocapture-browser

    // yarn
    yarn remove @amplitude/plugin-autocapture-browser
    ```

    Remove the initialization code:

    ```javascript
    // Remove the following lines of code
    import { autocapturePlugin } from '@amplitude/plugin-autocapture-browser';

    amplitude.add(autocapturePlugin());
    ```
