To establish a scalable approach for defining properties, you can use the **Google Tag: Event Settings** variable in GTM. GTM **Google Tag: Event Settings** variable provides a way to let you reuse the event settings in multiple tags. [More details](https://support.google.com/tagmanager/answer/13438771?hl=en). You can take advandate of it to create properties and reuse it across several tags.

The format of **Google Tag: Event Settings** variable:

```javascript
    {
        'eventPropKey' : 'eventPropValue',
        'otherEventPropKey': 'otherEventPropValue',
        'user_properties': {
            'user_property_key': 'user_property_value'
        }
    }
```