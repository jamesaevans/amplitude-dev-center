### Bitmap Capture

!!!info "Bitmap Capture is disabled by default"
    Enabling bitmap capture may increase the amount of CPU and memory used by the Session Replay SDK. This performance will be improved in future releases.

To enable bitmap capture, use one or more of the following

1. Set a `internalOptions.bitmapViewFilter`. E.g. `SessionReplay(internalOptions=InternalOptions(bitmapViewFilter = ViewFilters.ImageViewFilter()))`.
2. In Android XML, add `android:tag="amp-bitmap""` to your view. E.g. `<View android:tag="amp-bitmap"></View>`
3. In Compose layouts, add a `Modifier.ampBitmap()` to the view `modifiers`. E.g. `           Checkbox(checked = true, modifier = Modifier.ampBitmap())`
