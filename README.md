# React Native Background Location Pro

**Production-grade background location tracking for React Native that survives app kills, reboots, and offline periods, with no third-party tracking SDKs.**

Android and iOS are both shipping. Buy one platform or get both in the Best Value Edition — see [Get access](#-get-access).

![React Native](https://img.shields.io/badge/React%20Native-0.88-61DAFB?logo=react&logoColor=white)
![New Architecture](https://img.shields.io/badge/New%20Architecture-TurboModules-61DAFB?logo=react&logoColor=white)
![JSI](https://img.shields.io/badge/JSI-direct%20native%20calls-blueviolet)
![Kotlin](https://img.shields.io/badge/Android-Kotlin-7F52FF?logo=kotlin&logoColor=white)
![Swift](https://img.shields.io/badge/iOS-Swift-FA7343?logo=swift&logoColor=white)
![Android](https://img.shields.io/badge/Android-shipping-3DDC84?logo=android&logoColor=white)
![iOS](https://img.shields.io/badge/iOS-shipping-000000?logo=apple&logoColor=white)
![License](https://img.shields.io/badge/License-Commercial-orange)

---

## The problem

If you have shipped background location on mobile, you have probably hit these:

- **The OS kills your app** and tracking silently stops, so nobody notices until the data has gaps.
- **Points are lost while offline**, in tunnels, basements, or on weak networks.
- **Uploads get duplicated** on retries, so your backend fills up with repeated points.
- **Battery drains** because every GPS fix is stored and sent, even when the phone isn't moving.

Most tracking SDKs are expensive, closed, or break on newer OS versions. This module solves these problems natively, and you own the code.

---

## Platform support

| | Android | iOS |
| --- | --- | --- |
| Status | **Shipping** | **Shipping** |
| Language | Kotlin | Swift + Objective-C++ bridge |
| Architecture | **New Architecture only** — TurboModule + JSI, no legacy bridge | **New Architecture only** — `codegenConfig.ios.modulesProvider` |
| Native layer | Kotlin foreground service + FusedLocationProvider | Swift `CLLocationManager` + `CLBackgroundActivitySession` (iOS 17+) |
| Bridge | JSI TurboModule | TurboModule via Objective-C++ (`RCTLocationTracker`) |
| Offline queue | Room | System `sqlite3` |
| Self-healing | `START_STICKY` service + `AlarmManager` watchdog + boot / update receivers | Significant-change relaunch + `BGAppRefreshTask` + heartbeat watchdog |

Built and tested on React Native 0.88 with the New Architecture enabled. There is no Paper /
legacy-bridge path on either platform — the module is codegen-driven on both sides and no
`NativeModules` shim is involved. Both platforms share the same core JS API; iOS adds
`requestLocationPermission` and authorization status fields (When-In-Use / Always, precise location).

Unlike Android, iOS has no foreground service. Background collection depends on the `location`
background mode and the **Always** authorization; this is a platform constraint, not an
implementation shortcut, and it is documented in the iOS build's own README.

---

## Key capabilities

- **Keeps tracking with the app closed.** It runs as a native service, independent of the JS layer — a Kotlin foreground service on Android, `CLLocationManager` with background mode on iOS.
- **Self-healing.** Tracking restarts on its own after a crash, a phone reboot, or an app update. On iOS this needs **Always** location permission, and iOS never relaunches an app the user force-quit from the app switcher until it is opened again.
- **Offline-first.** Every point is saved on the device first, so nothing is lost without network.
- **No duplicate uploads.** Batched sync stays safe across retries and flaky connections.
- **Battery-friendly smart filtering.** Only meaningful movement is recorded.
- **Live map dashboard.** Includes a backend with a real-time map to watch devices move.
- **Modern React Native.** Built on the New Architecture (JSI / TurboModule) with a typed API.

---

## Tested scenarios

Android:

| Scenario | Result |
| --- | --- |
| Airplane mode for several minutes while moving | Passed: all points delivered after reconnecting |
| App process killed by the system | Passed: tracking resumes automatically |
| Phone rebooted without opening the app | Passed: tracking resumes automatically |
| App updated to a new version | Passed: tracking resumes automatically |
| Phone idle for a long period | Passed: no junk points, tracking stays alive |
| Flaky or captive-portal network | Passed: data held safely until a real connection |
| Repeated uploads of the same data | Passed: zero duplicates on the server |

iOS: offline buffering and duplicate-free uploads behave the same way. Recovery after a reboot or a
system kill relies on **Always** permission (significant-change relaunch), and a user force-quit stops
tracking until the app is reopened — an iOS rule that applies to every app.

---

## Demo

Short clips from the reference implementation. Both platforms use the same core JS API and the same
ingestion server, so the dashboard output is identical.

<table>
<tr>
<td width="50%" align="center">

**Android** — Kotlin foreground service

<a href="assets/demo.mp4">
  <img src="assets/demo-preview.gif" alt="Android background location tracking demo" width="320" />
</a>

[Watch the Android demo (MP4)](assets/demo.mp4)

</td>
<td width="50%" align="center">

**iOS** — Swift `CLLocationManager`

<a href="assets/demo-ios.mp4">
  <img src="assets/demo-ios-preview.gif" alt="iOS background location tracking demo" width="320" />
</a>

[Watch the iOS demo (MP4)](assets/demo-ios.mp4)

</td>
</tr>
</table>

What the demo shows: tracking started in the foreground, then the app is backgrounded and the process
is killed by the system. Points keep landing on the live map, and the queue drains on reconnect.

---

## What's included

Every edition includes:

- The React Native JS API (typed TurboModule spec) and a ready-to-use live dashboard screen
- A backend ingestion server with a real-time live map
- A setup and run guide
- Lifetime updates to the repositories you bought

Plus, per edition:

| Edition | Native code | Private repository access |
| --- | --- | --- |
| **Android Edition** | Complete Android tracking module (Kotlin, New Architecture) | Android repository |
| **iOS Edition** | Complete iOS tracking module (Swift + Objective-C++ TurboModule) | iOS repository |
| **Best Value Edition** | Both modules | Both repositories |

---

## 🚀 Get access

Pay once, no subscription. Pick an edition, then the payment option that matches your location.

| Edition | What you get | USD (GitHub Sponsors) | INR (UPI) |
| --- | --- | --- | --- |
| **Android Edition** | Android module + JS API + server | **$39** | **₹3,000** |
| **iOS Edition** | iOS module + JS API + server | **$59** | **₹5,000** |
| **Best Value Edition** ⭐ | Android + iOS, both repositories | **$89** (save $9) | **₹7,000** (save ₹1,000) |

### 🌎 Option A: International developers (outside India), via GitHub Sponsors

Pay securely through GitHub Sponsors with any credit card, debit card, or PayPal.

👉 **[Sponsor on GitHub (one-time)](https://github.com/sponsors/126punith)**

> **Important:** choose the **One-time** tab and select the tier for your edition: **$39** (Android), **$59** (iOS), or **$89** (Best Value). Do **not** pick a monthly sponsorship. This is a single payment, not a subscription.

**How access works**

1. Open the link above, switch to **One-time**, and complete the sponsorship for your edition.
2. I personally confirm that your sponsorship and payment have come through.
3. I then add your GitHub account as a collaborator to the repository (or both repositories for Best Value) that matches your tier, usually within 24 hours.
4. Accept the invite from your email or from [github.com/notifications](https://github.com/notifications).

*No need to send your username, because GitHub shows me which account sponsored and which tier. If you sponsored from a different account than the one you want access on, email [punithm300@gmail.com](mailto:punithm300@gmail.com).*

### 🇮🇳 Option B: Indian developers (UPI / GPay)

Pay directly via UPI: **₹3,000** (Android), **₹5,000** (iOS), or **₹7,000** (Best Value).

1. Scan the QR code below with any UPI app (GPay, PhonePe, Paytm).
2. Enter the amount for your edition and make a one-time payment.
3. Email a screenshot of the successful payment, the **edition** you bought, and your **GitHub username** to **[punithm300@gmail.com](mailto:punithm300@gmail.com)**.
4. You'll be added as a collaborator to the matching private repository (or both for Best Value) after the payment is verified.

<p align="center">
  <img src="assets/upi-qr.jpeg" alt="GPay / UPI QR code" width="260" />
</p>

---

## FAQ

**Is this a subscription?**
No. Every edition is a one-time payment with lifetime access to its repository and updates. On GitHub Sponsors, make sure you pick the one-time tier ($39, $59, or $89), not a monthly one.

**Which edition should I buy?**
Buy the Android or iOS Edition if your app ships on one platform. If you ship on both, the Best Value Edition costs less than buying the two separately.

**Can I use it in commercial apps?**
Yes. You can use it in personal and commercial projects.

**Can I share or resell the code?**
No. Redistributing, reselling, or publishing the source code is not allowed.

**Does it support iOS?**
Yes. iOS is shipping: buy the iOS Edition on its own, or the Best Value Edition for Android and iOS together.

**I paid but haven't got access yet.**
Email [punithm300@gmail.com](mailto:punithm300@gmail.com) with your GitHub username, the edition you bought, and a Sponsors receipt or UPI screenshot.

---

## License

### Commercial Source License Agreement

Copyright (c) 2026 Punith Manthri. All rights reserved.

By purchasing, downloading, or accessing the source code of **React Native Background Location Pro** (the "Software"), you (the "Licensee") agree to be bound by the terms and conditions of this Commercial Source License Agreement.

#### 1. Grant of License

Subject to a valid one-time payment, the Licensor (Punith Manthri) grants the Licensee a perpetual, non-exclusive, worldwide, non-transferable license to:

- Use, modify, and integrate the Software source code into personal projects.
- Use, modify, and integrate the Software source code into commercial/production applications owned by the Licensee or built for a single corporate client.

#### 2. Restrictions & Prohibitions

The Licensee is strictly forbidden from engaging in the following actions:

- **No Redistribution:** You cannot redistribute, publish, upload to public repositories (such as public GitHub repos), or make the underlying source code accessible to third parties.
- **No Reselling:** You cannot resell, sub-license, rent, lease, or commercially exploit the Software source code as a standalone asset, template, module, or starter kit.
- **No Sublicensing:** A single purchase covers one individual developer or organization. You cannot purchase one copy and distribute the source code across an entire external network of independent developers.

#### 3. Intellectual Property

The Software and all native source blueprints (including Kotlin and Swift modules, JSI bindings, and Express backend telemetry configurations) are and remain the exclusive intellectual property of the Licensor.

#### 4. Termination

Any breach of this License Agreement automatically terminates your rights under this license. Upon termination, you must immediately cease using the Software and securely delete all copies of the source code in your possession.

#### 5. Limitation of Liability

The Software is provided "as is", without warranty of any kind, express or implied. In no event shall the Licensor be liable for any claim, damages, or other liability arising from, out of, or in connection with the Software.
