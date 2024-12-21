# GHL Calendar Setup with Google Tag Manager

This guide provides a step-by-step process for configuring your Google Tag Manager (GTM) to detect and manipulate GHL Calendar elements on your web pages.

---

## Project Description

GoHighLevel booking calendars are often considered too simple. A common complaint is that users get confused about the booking times because they read them too quickly. This often results in users booking a night slot in their timezone but failing to appear for the calls, mistakenly believing the booked time is during the day. 

To address this issue, this method adds a night emoji 🌙 to time slots between 8 PM and 12 AM, and hides the slots between 12 AM and 6 AM to prevent accidental bookings. 

### Requirements

You need Google Tag Manager (GTM) to implement this fix. Please note that only calendars embedded on pages that include GTM will have this functionality. Alternatively, you can embed the script directly into your pages and skip GTM.

---

## 1. Define a Variable to Detect the Existence of the GHL Calendar on Pages

1. Navigate to your **GTM container** -> **Variables**, and create a new variable named `GHL Calendar exists on the page`.

2. Configure the variable as follows:
   - **Variable Type:** Element Visibility
   - **Selection Method:** CSS Selector
   - **Element Selector:** `.c-calendar`
   - **Output Type:** True/False
   - **Minimum Percent Visible:** 50%
   - **Format Value:** Convert true to `1` and false to `0`

3. Save the variable.

![Variable Definition](./01%20-%20Variable%20Definition.png)

---

## 2. Define a Trigger Based on the Variable

1. Go to **GTM Container** -> **Triggers**, and add a new trigger named `DOM - GHL Sleeping Hours`.

2. Configure the trigger as follows:
   - **Trigger Type:** Page View - Window Loaded
   - **Trigger Fires On:** Some Window Loaded events

3. Set the condition:
   - `GHL Calendar exists on the page` equals `1`

4. Save the trigger.

![Trigger Definition](./02%20-%20Trigger%20Definition.png)

---

## 3. Define and Use the Tag

1. Go to **GTM Container** -> **Tags**, and add a new tag named `GHL Disappear Night Time Slots`.

2. Configure the tag as follows:
   - **Tag Type:** Custom HTML
   - Paste the contents of `script.txt` into the HTML area.
   - Check the option **Support document.write**.

3. Add the trigger `DOM - GHL Sleeping Hours`.

4. Save the tag.

![Tag Definition](./03%20-%20Tag%20definition.png)

---

## 4. Preview and Publish the Changes

1. Preview the changes on the GHL pages that include calendars.
2. Ensure the GTM scripts are already set up on those pages; otherwise, the solution will not work on individual calendar pages.
   - Calendars must be placed inside a page (either an individual page or within a funnel) for the script to function properly.
3. After previewing the changes, publish the container and enjoy!

---

