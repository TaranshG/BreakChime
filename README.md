# BreakChime ⏰

**A Chrome extension that helps you take healthier screen breaks without interrupting your workflow.**

Ever get so focused on studying, coding, or working that you forget to look away from your screen? I built BreakChime to solve that problem.

BreakChime provides customizable break reminders, background timers, notification sounds, and simple controls to help you build better screen-break habits.

**[Install from the Chrome Web Store](https://chromewebstore.google.com/detail/breakchime-screen-break-r/bpfpaalmndaecjcjmhiphfdgcfajiapf)** | **[Website](https://breakchime.vercel.app)**

## 📸 Screenshots

*Add the same screenshots used on the Chrome Web Store here.*

Ideally, show:
- The main timer and countdown
- Reminder and notification settings
- Break statistics or progress features

## ✨ Features

- **Customizable break reminders** — Set your preferred reminder interval and break duration.
- **Background timers** — Reminders continue working even when the extension popup is closed.
- **Pause, resume, and reset** — Manage reminders without losing your place.
- **Snooze functionality** — Delay a reminder when you're in the middle of something.
- **Sound notifications** — Choose a chime, preview sounds, or turn audio off.
- **Dark mode** — Customize the extension's appearance.
- **Break tracking** — View your break statistics and progress.

## 🛠 Built With

- **JavaScript, HTML, CSS** — Extension interface and functionality
- **Chrome Extensions Manifest V3** — Browser extension architecture
- **Chrome Alarms API** — Scheduling background reminders
- **Chrome Storage API** — Persisting settings and timer state
- **Chrome Notifications API** — Displaying break reminders
- **Chrome Offscreen API** — Playing audio while the popup is closed
- **Node.js test runner** — Automated testing with mocked browser APIs

## ⚙️ Engineering Highlights

### 1. Reliable background timers

Chrome extensions can't rely on their popup staying open.

I designed BreakChime's timer around Chrome service workers, alarms, and persistent storage so reminder state survives popup closures and background worker restarts.

Pausing preserves the remaining countdown, and resuming continues from that point instead of restarting the timer.

### 2. Background audio and notifications

BreakChime uses Chrome's Offscreen API to play bundled notification sounds even when the popup isn't open.

The audio system handles offscreen document reuse and concurrent requests, while avoiding duplicate notification sounds.

### 3. State management and testing

The extension preserves user preferences and timer state across normal browser activity.

Automated tests cover timer behavior, notification interactions, muted reminders, audio failures, and concurrent background operations.

These tests validate extension logic with mocked Chrome APIs; actual operating-system notifications and speaker output are tested separately.

## 🚀 Getting Started

1. [Install BreakChime from the Chrome Web Store](https://chromewebstore.google.com/detail/breakchime-screen-break-r/bpfpaalmndaecjcjmhiphfdgcfajiapf).
2. Open Chrome's Extensions menu and pin BreakChime.
3. Open the extension and configure your reminder interval and break duration.
4. Enable sound notifications if desired.
5. Start working — BreakChime will remind you when it's time for a break.

**Reminder controls**

- **Pause:** Freeze the current countdown.
- **Resume:** Continue from the remaining time.
- **Reset:** Restart the current reminder interval.
- **Snooze:** Postpone the current reminder.

Changing the reminder interval starts a new interval, while preserving the paused state when applicable. Other preferences can be updated without restarting a paused countdown.

## 💻 Running Locally

1. Clone this repository.
2. Open `chrome://extensions` in Chrome.
3. Enable **Developer mode**.
4. Click **Load unpacked**.
5. Select the extension's source directory.

To run the available development checks:

```bash
node --test *.test.cjs
node --check popup.js
```

## 🔔 Notifications and Troubleshooting

BreakChime requires Chrome to be running and your computer to be awake for timely reminders. Closing the extension popup is fine; closing the browser or putting the computer to sleep may delay reminders.

If notifications don't appear:

- **macOS:** Check System Settings → Notifications and Focus settings for your browser.
- **Windows:** Check Settings → System → Notifications and Do not disturb.
- **No sound:** Enable Sound Notifications in BreakChime, try Test Sound, and check your system volume and audio output.
- **Still having issues?** Restart the browser and use the **Report bug** option in BreakChime's settings.

BreakChime uses Chrome's notification and offscreen APIs rather than external notification or audio services.

## 💡 Why I Built It

I originally built BreakChime because I'd spend hours coding or studying without remembering to take breaks.

What started as a small personal solution turned into a published Chrome extension used by hundreds of people.

Building it taught me a lot about browser APIs, background execution, persistent state, debugging, and making software reliable outside the happy path.

---

**Built by [Taransh Goyal](https://github.com/TaranshG)**

[Chrome Web Store](https://chromewebstore.google.com/detail/breakchime-screen-break-r/bpfpaalmndaecjcjmhiphfdgcfajiapf) · [Website](https://breakchime.vercel.app) · [LinkedIn](https://linkedin.com/in/taransh-goyal)
