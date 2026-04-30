# iOS Sleep Data Receiver

This blueprint creates a high-logic script in Home Assistant designed to receive sleep and alarm data from an iOS Shortcut. Unlike basic integrations, this handles complex calculations like **Timezone offsets** (comparing your iPhone's location to your HA server) and **Skip Logic** (detecting when an alarm is disabled for "Tomorrow Only").

## 🚀 Setup Instructions

### 1. Create the Required Helpers

Before setting up the script, you must create two helpers in Home Assistant (**Settings > Devices & Services > Helpers > Create Helper > Date and/or Time**):

- **Next Alarm:** `input_datetime.next_alarm` (Select "Date and time")
- **Skipped Alarm:** `input_datetime.skipped_alarm` (Select "Date and time")

### 2. Install the Blueprint & Script

1.  **Import:** Click the badge below to import this blueprint to your instance:
    [![Import Blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/ytsymbaliuk/homeassistant/raw/refs/heads/blueprints/ios-sleep-data-receiver/blueprints/ios-sleep-data-receiver/ios-sleep-data-receiver.yaml)
2.  **Create Script:** Go to **Settings > Automations & Scenes > Scripts** and create a new script from the blueprint.
3.  **Configure:** Map the input entities to the helpers you created in Step 1.

### 3. Install the iOS Shortcut

This shortcut acts as the "sender." It gathers your Health data and pushes it to the script you just created.

- 👉 **[Download iOS Shortcut](https://www.icloud.com/shortcuts/98ace58b387943d5947dc5f845f45428)**
- **Configuration:** When importing, enter your Home Assistant URL and the name of the script you created (e.g., `script.ios_sleep_sync`).

---

## 🛠 How to Automate

To keep your data synced without thinking about it, set up a **Personal Automation** in the iOS Shortcuts app:

1.  Open **Shortcuts** app > **Automation** tab > **+**.
2.  Choose **Sleep** (e.g., "When Waking Up") or **App** (e.g., "When Clock is closed").
3.  Set it to **Run Immediately** (disable "Ask Before Running").
4.  Action: **Run Shortcut** -> select the "iOS Sleep Data Receiver" shortcut.

## 🤝 Credits & Acknowledgments

This logic is based on the collaborative effort of the Home Assistant Community.

- **Original Concept:** [DIY-techie](https://community.home-assistant.io/u/diy-techie)
- **Timezone & Multi-schedule Logic:** [holblin](https://community.home-assistant.io/u/holblin)
- **Discussion Thread:** [Sync IOS 17 Sleep alarm to HA (take 2)](https://community.home-assistant.io/t/sync-ios-17-sleep-alarm-to-ha-take-2/715690/9)
