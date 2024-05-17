---
title: HubSpot Event Streaming v2
description: Send Amplitude events to HubSpot automatically with just a few clicks.
---

[HubSpot](https://www.HubSpot.com/) is an easy to use and powerful CRM platform that enables scaling companies to sell, market and provide customer service from a unified UI. Amplitude's HubSpot streaming integration enables you to forward your Amplitude events and event properties straight to HubSpot with just a few clicks.

!!!info "This integration is in Closed Beta"

    This feature is in Closed Beta and is in active development. Email integrations@amplitude.com if you are interested. Unlike the [HubSpot streaming integration](https://www.docs.developers.amplitude.com/data/destinations/HubSpot-event-streaming/), this integration will automatically create the necessary custom event definitions and properties in HubSpot, rather than requiring they be created manually. 

## Use cases

1. **Personalized Marketing:** With the ability to track user behavior and capture user and event properties in Amplitude, businesses can create highly personalized and targeted marketing campaigns in HubSpot. This can lead to increased engagement, conversions, and customer loyalty.
2. **Lead Scoring and Nurturing:** By tracking user behavior and capturing user and event properties in Amplitude, businesses can score and prioritize leads based on their level of engagement and interests. This can help businesses to optimize their lead nurturing efforts and increase their chances of closing deals.
3. **Customer Retention:** By tracking user behavior and capturing user and event properties in Amplitude, businesses can identify customers who are at risk of churning and take proactive steps to retain them. For instance, businesses can trigger personalized emails or ads to offer discounts or incentives to encourage customers to stay engaged with the product or service.

## Considerations

Keep these things in mind when sending events to HubSpot:

- You must enable this integration in each Amplitude project you want to use it in.
- Events from Amplitude appear as Custom Behavioral Events in HubSpot. 
- A HubSpot Enterprise Marketing Hub account is required to send Custom Behavioral Events.
- Relevant limits for HubSpot events are:
    - HubSpot enforces strict API rate limits. You can find more information about these limits [here](https://developers.HubSpot.com/docs/api/usage-details).
    - HubSpot allows up to 50 custom properties for each custom event.
- Amplitude sends selected event and user properties along with the event.
- Amplitude targets an end-to-end p95 latency of 60s. This means 95% of Events streamed deliver to HubSpot within 60s or less. Amplitude has internal processes, monitors, and alerts in place to meet this target.   

## Setup

### Amplitude setup

1. In Amplitude Data, click **Catalog** and select the **Destinations** tab.
2. In the Event Streaming section, click **HubSpot**.
3. Enter a sync name, then click Create **Sync**.
4. Choose a HubSpot Account ID or authenticate with HubSpot. If you already have an existing Account ID, you will need to re-authenticate to grant additional permissions from Hubspot.
5. Toggle the **Send events** filter to select the events to send.
6. Under the **Select & filter events** section, select which Amplitude Events you would like to map to HubSpot. Provide a HubSpot Internal Event Name which corresponds with this Amplitude Event that you’ve selected. HubSpot recommends choosing the events that are most important to your use case.
7. Under the **Map properties to destinations**, select which Event Properties you would like to send. The HubSpot identifier for this object must be at least one of the following: User Token, Email or Object ID.
8. Under the **Select additional properties** section, select any extra event and user properties you want to send to HubSpot. If you don't select any properties here, Amplitude doesn't send any. Transformed event properties and transformed user properties aren't supported.
9. When finished, enable the destination and **Save**.

## Use custom behavioral event data in HubSpot

- Click here to learn more about how you can [analyze custom behavioral events](https://knowledge.HubSpot.com/analytics-tools/analyze-custom-behavioral-events) in HubSpot.
  
### Report on custom events

Analyze custom event completions from the custom events tool, and event data is available in the custom report builder and attribution reports.

Learn more about [analyzing your custom events](https://knowledge.HubSpot.com/analytics-tools/analyze-custom-behavioral-events).

### View event completions on the contact timeline

Event completions appear on the contact record timeline, along with any properties that were populated.

To view event details on the contact timeline:

- [Navigate to a contact record](https://knowledge.HubSpot.com/records/work-with-records) that has completed a custom event.
- To filter a contact timeline by completed events, click **Filter activity**, then select **Custom event**.
- In the contact timeline, click to expand the **event** to display the event details.

### Use custom events in workflows

In a workflow, you can delay based on custom event completions using a [Delay until event happens action](https://knowledge.HubSpot.com/workflows/use-delays) or an event enrollment trigger.

1. In your HubSpot account, navigate to **Automation > Workflows**.
2. Click the **name** of a workflow. Or, learn how to create a new workflow.
3. In the workflow editor, click the **+ plus icon** to add a workflow action.
4. In the right panel, select **Delay until the event happens**.
5. Configure the delay:
    - Click the **Event** dropdown menu, then select a **custom behavioral event**.
    - Then, select the **event property** that you want to delay on.
    - Select the **filter** for the event property.
    - Click **Apply filter**.
    - Select the **maximum wait time**, or select the **Delay as long as possible checkbox**.
6. Click **Save**.
