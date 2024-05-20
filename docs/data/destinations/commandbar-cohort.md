---
title: Send Cohorts to CommandBar
description: Sync cohorts from Amplitude to CommandBar
status: new
---

[CommandBar](https://www.commandbar.com/) is an AI-powered user assistance platform that makes your product easier to use, without the old-school method of interrupting popups that users quickly close. Activate and retain more users through personalized, interactive in-product experiences that mimic what a human assistant would do. For example, Copilot chat (the only chatbot that can co-browse with users) and just-in-time proactive nudges that trigger when a user appears confused. This integration lets you sync cohorts from Amplitude to CommandBar to personalize CommandBar experiences using the same cohorts you analyze in Amplitude.

!!!Tip

    This integration is maintained by CommandBar. Contact the [CommandBar](https://www.commandbar.com/) for support with this integration. 

## Considerations

- You must enable this integration in each Amplitude project you want to use it in.
- You will need to have a paid CommandBar plan to enable this integration.
- CommandBar only accepts email addresses as the identifier. This means the User_ID or user property you select in Amplitude must contain an email address.

## Setup

### CommandBar setup

1. Log in to your **CommandBar** account.
2. In CommandBar, navigate to Integrations.
3. Find Amplitude then click “Configure”
4. Copy the API Key and AppCode to your clipboard.

### Amplitude setup

1. In Amplitude Data, click **Catalog** and select the **Destinations** tab.
2. In the Cohort section, click **CommandBar**.
3. Click **Add another destination**.
4. Enter **Name** and paste in the **API key** you copied from **CommandBar**.
5. Map the Amplitude User ID field to the Humanic.ai User ID field
6. Save when finished.

## Send a cohort

To sync your first cohort, follow these steps:

1. In Amplitude, open the cohort you want to sync, then click **Sync**.
2. Select **CommandBar**, then click **Next**
3. Choose the account you want to sync to
4. Choose the sync cadence.
5. When finished, save your work.

## Locating your cohort in CommandBar

Cohorts are available for use across many parts of CommandBar.
1. **Audiences:** From https://app.commandbar.com/editor/audiences, you can edit or create an audience. In the condition dropdown, select “Amplitude Cohort” and then select your desired cohort. Audiences can be used to personalize nudge targeting, HelpHub recommendation sets, Copilot behavior, and more.
2. **Nudges:** For any nudge (e.g., product tour, survey, or checklist), you can use your Amplitude cohort in the “Targeting” → “Who” rules. After choosing a “Custom” condition, you can select “Amplitude Cohort” and then select your desired cohort.

## Use Cases

1. **Feature Adoption:**
  - **Scenario:** After poring through analytics reports, you have an epiphany – a particular cohort of users in Amplitude frequently visits your app, but never discovers your team’s sickest feature!
  - **Unlock:** You tailor tooltips to this cohort with CommandBar, helping them discover the feature and achieve greatness with it.
2. **User Onboarding:**
  - **Scenario:** New users are placed into an "onboarding" cohort in Amplitude.
  - **Unlock:** You create a step-by-step onboarding guide in CommandBar, providing contextual help and tips exactly when users need them (and without annoying them). Even better if you can further segment the “new users” cohort into thinner slices. For example, based on an onboarding survey (which you can also build with CommandBar), or the channel through which they created an account (for example – direct, blog post, ad, etc).
3. **Customer Support Efficiency:**
  - **Scenario:** Support tickets are going through the roof. Your team creates a cohort in Amplitude to better understand users who have submitted multiple support tickets on a specific issue or from a specific page.
  - **Unlock:** You create some custom Playbooks for Copilot chat that handle the scenarios your users are asking about (including the ability for Copilot to lainch interactive tours).
4. **Retention Campaigns:**
  - **Scenario:** A cohort of users in Amplitude show signs of inactivity and are flagged as high churn risk. 
  - **Unlock:** With CommandBar, you use Nudges to craft re-engagement messages and offer these users discounted pricing.
5. **Freemium to Premium:**
  - **Scenario:** The team has seen slower-than-expected conversion rates for the “Free tier” cohort.
  - **Unlock:** Using CommandBar Tooltips, you sprinkle visual cues throughout the app to indicate features that are only available to premium users. But you don’t stop there! You develop a series of in-app paywalls that catch users in various flows to nudge them towards a trial of your premium tier.
