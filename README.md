# ₿ Bitcoin Converter (BTC • SAT • THB)

A professional-grade, real-time financial tool designed for the "Bitcoin Standard." This converter allows users to instantly calculate values between Bitcoin (BTC), Satoshis (SAT), and Thai Baht (THB) using live market rates.

[![Live Demo](https://img.shields.io/badge/demo-live-orange?style=for-the-badge)](https://converter.sorawisit.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

---

## ✨ Features

* **🔄 Triple-Sync Conversion:** Real-time, bidirectional conversion between THB, SAT, and BTC.
* **📈 Live Market Data:** Integrated with the **Bitkub API** for precise Thai Baht market rates and **Mempool.space** for network fee estimation.
* **⏳ Halving Countdown:** Dynamic timer tracking the next Bitcoin block reward halving.
* **🎯 Savings Goals:**
    * **Purchasing Power Comparison:** Built-in grid comparing BTC value to everyday items (Coffee, Gold, Tesla).
    * **Custom Goals:** Persistent user-defined savings goals saved via `localStorage`.
* **🛡️ Supply Integrity Logic:** Hard-coded logic preventing calculations exceeding the total 21,000,000 BTC supply.
* **🌓 Advanced UI/UX:**
    * **Glassmorphism Design:** Modern, responsive interface with blurred backdrops.
    * **Theme Engine:** Supports Light, Dark, and System modes with a "zero-flash" initialization script.
    * **Precision Inputs:** Custom input masking for financial formatting (commas and decimal handling).

---

## 🛠️ Tech Stack

| Layer | Technology |
| :--- | :--- |
| **Frontend** | HTML5 / Vanilla JavaScript (ES6+) |
| **Styling** | Custom CSS3 (CSS Variables, Grid, Flexbox) |
| **Data Fetching** | Fetch API (Asynchronous) |
| **Storage** | Browser LocalStorage (for Custom Goals & Themes) |
| **Typography** | Inter & JetBrains Mono (for financial clarity) |

---

## 📊 API Sources

This project relies on high-uptime public APIs to provide accurate financial data:
* **Market Price:** `api.bitkub.com` (THB/BTC pair)
* **Network Fees:** `mempool.space` (Fastest fee recommended)
* **Halving Estimates:** Calculated locally based on target block dates.

---

## 📂 Project Structure

```text
├── index.html        # Single-file architecture (HTML, CSS, and JS logic)
├── favcon.webp       # Site branding
└── README.md         # Project documentation
