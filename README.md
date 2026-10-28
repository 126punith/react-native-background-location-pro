# React Native Background Location Pro

**Production-grade background location tracking for React Native (Android) that survives app kills, reboots, and offline periods, with no third-party tracking SDKs.**

![React Native](https://img.shields.io/badge/React%20Native-New%20Architecture-61DAFB?logo=react&logoColor=white)
![JSI](https://img.shields.io/badge/JSI-TurboModule-blueviolet)
![Kotlin](https://img.shields.io/badge/Native-Kotlin-7F52FF?logo=kotlin&logoColor=white)
![Android](https://img.shields.io/badge/Android-14%2B%20ready-3DDC84?logo=android&logoColor=white)
![License](https://img.shields.io/badge/License-Commercial-orange)

---

## The problem

If you have shipped background location on Android, you have probably hit these:

- **The OS kills your app** and tracking silently stops, so nobody notices until the data has gaps.
- **Points are lost while offline**, in tunnels, basements, or on weak networks.
- **Uploads get duplicated** on retries, so your backend fills up with repeated points.
- **Battery drains** because every GPS fix is stored and sent, even when the phone isn't moving.

Most tracking SDKs are expensive, closed, or break on newer Android versions. This module solves these problems natively, and you own the code.

---

## Key capabilities

- **Keeps tracking with the app closed.** It runs as a native Kotlin foreground service, independent of the JS layer.
- **Self-healing.** Tracking restarts on its own after a crash, a phone reboot, or an app update.
- **Offline-first.** Every point is saved on the device first, so nothing is lost without network.
- **No duplicate uploads.** Batched sync stays safe across retries and flaky connections.
- **Battery-friendly smart filtering.** Only meaningful movement is recorded.
- **Live map dashboard.** Includes a backend with a real-time map to watch devices move.
- **Modern React Native.** Built on the New Architecture (JSI / TurboModule) with a typed API.

---

## Tested scenarios

| Scenario | Result |
| --- | --- |
| Airplane mode for several minutes while moving | Passed: all points delivered after reconnecting |
| App process killed by the system | Passed: tracking resumes automatically |
| Phone rebooted without opening the app | Passed: tracking resumes automatically |
| App updated to a new version | Passed: tracking resumes automatically |
| Phone idle for a long period | Passed: no junk points, tracking stays alive |
| Flaky or captive-portal network | Passed: data held safely until a real connection |
| Repeated uploads of the same data | Passed: zero duplicates on the server |

---

## Demo

<p align="center">
  <a href="assets/demo.mp4">
    <img src="assets/demo-preview.gif" alt="Background location tracking demo" width="320" />
  </a>
</p>
<p align="center"><a href="assets/demo.mp4"><b>Watch the full demo video (MP4)</b></a></p>

---

## What's included in the private repository

- The complete native Android tracking module (Kotlin)
- The React Native JS API and a ready-to-use live dashboard screen
- A backend ingestion server with a real-time live map
- A step-by-step setup and integration guide
- Lifetime updates to the repository

---

## 🚀 Get access

Pay once to get access to the complete private repository. Choose the option that matches your location.

### 🌎 Option A: International developers (outside India), via GitHub Sponsors

Pay securely through GitHub Sponsors with any credit card, debit card, or PayPal.

👉 **[Sponsor on GitHub: one-time $39 USD](https://github.com/sponsors/126punith)**

> **Important:** choose the **One-time** tab and select the **$39** tier. Do **not** pick a monthly sponsorship. This is a single payment, not a subscription.

**How access works**

1. Open the link above, switch to **One-time**, and complete the **$39 USD** sponsorship.
2. I personally confirm that your sponsorship and payment have come through.
3. I then add your GitHub account as a collaborator to the private repository, usually within 24 hours.
4. Accept the invite from your email or from [github.com/notifications](https://github.com/notifications).

*No need to send your username, because GitHub shows me which account sponsored. If you sponsored from a different account than the one you want access on, email [punithm300@gmail.com](mailto:punithm300@gmail.com).*

### 🇮🇳 Option B: Indian developers (UPI / GPay)

Pay directly via UPI: **₹3,000 INR**.

1. Scan the QR code below with any UPI app (GPay, PhonePe, Paytm).
2. Make a one-time payment of **₹3,000**.
3. Email a screenshot of the successful payment along with your **GitHub username** to **[punithm300@gmail.com](mailto:punithm300@gmail.com)**.
4. You'll be added as a collaborator to the private repository after the payment is verified.

<p align="center">
  <img src="assets/upi-qr.jpeg" alt="GPay / UPI QR code for ₹3,000" width="260" />
</p>

---

## FAQ

**Is this a subscription?**
No. It's a one-time payment with lifetime access to the repository and its updates. On GitHub Sponsors, make sure you pick the one-time $39 tier, not a monthly one.

**Can I use it in commercial apps?**
Yes. You can use it in personal and commercial projects.

**Can I share or resell the code?**
No. Redistributing, reselling, or publishing the source code is not allowed.

**Does it support iOS?**
The current release targets Android. Email me if you need iOS.

**I paid but haven't got access yet.**
Email [punithm300@gmail.com](mailto:punithm300@gmail.com) with your GitHub username and a Sponsors receipt or UPI screenshot.

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

The Software and all native source blueprints (including Kotlin modules, JSI bindings, and Express backend telemetry configurations) are and remain the exclusive intellectual property of the Licensor.

#### 4. Termination

Any breach of this License Agreement automatically terminates your rights under this license. Upon termination, you must immediately cease using the Software and securely delete all copies of the source code in your possession.

#### 5. Limitation of Liability

The Software is provided "as is", without warranty of any kind, express or implied. In no event shall the Licensor be liable for any claim, damages, or other liability arising from, out of, or in connection with the Software.
