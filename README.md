# 🛠️ Ultra-Optimized Minecraft 1.21.11 Server Setup & Performance Guide

Are you tired of continuous server lag, low TPS, and frustrating Java runtime environment errors while trying to host a Minecraft 1.21.11 server for your friends? 

Running a vanilla server straight out of the box usually results in heavy CPU usage and rubberbanding. This repository provides the essential performance tweaks and architectural advice to help you run a rock-solid, **20 TPS Minecraft server** on personal hardware.

---

## ⚡ Too Lazy to Configure? Skip the Headache!

If you don't want to spend hours modifying configs, fixing port-forwarding issues, or debugging Java paths, I have already packaged everything into a clean, **1-Click Pre-Optimized Server Pack**.

### 🚀 What's Inside the 1-Click Pack:
* **Embedded Portable Java 21:** You don't even need to install Java on your Windows machine. Just click and run.
* **Deeply Tuned Kernels:** Pre-configured Paper/Purpur configuration files optimized for maximum entity performance and async chunk loading.
* **Network & IP Privacy Guard:** Built-in step-by-step guide for secure hosting (completely hides your home IP and prevents DDoS for free).
* **Pre-installed Essentials:** Anti-griefing protection ready out of the box.

👉 **[DOWNLOAD THE 1-CLICK PRE-OPTIMIZED SERVER PACK ON GUMROAD](https://nobrainbacon.gumroad.com/l/lsipw)**

---

## 🔍 Manual Optimization Checklist (Do It Yourself)

If you prefer to set up everything manually, follow these high-performance industry guidelines:

### 1. Ditch the Vanilla Core
Never run the official Mojang `vanilla.jar` for a multiplayer server. It operates on a single CPU thread and lags instantly with more than 3 players. 
* **Recommendation:** Use **Paper** or **Purpur**. They preserve 100% vanilla mechanics (clients don't need mods to join), but optimize entity AI, physics ticks, and hopper lagging algorithms.

### 2. Crucial Startup Flags (Aikar's Flags)
Do not use standard startup commands. You need to optimize the Java Virtual Machine (JVM) Garbage Collection to avoid severe lag spikes. Use Aikar's optimized flags in your startup script:

```bash
java -Xms6G -Xmx6G -XX:+UseG1GC -XX:+ParallelRefProcEnabled -XX:MaxGCPauseMillis=200 -XX:+UnlockExperimentalVMOptions -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:G1NewSizePercent=30 -XX:G1MaxNewSizePercent=40 -XX:G1HeapRegionSize=8m -XX:G1ReservePercent=15 -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=4 -XX:InitiatingHeapOccupancyPercent=15 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=5 -XX:SurviorRatio=32 -XX:+PerfDisableSharedMem -XX:MaxTenuringThreshold=1 -Dusing.aikars.flags=[https://mcflags.emc.gs](https://mcflags.emc.gs) -Daikars.new.flags=true -jar purpur.jar nogui
```

### 3. Essential Network Configuration Tweaks
Modify these settings within your server config files for immediate performance boosts:

* **`server.properties`:**
  * `network-compression-threshold: 256` (Reduces bandwidth strain on slower home Wi-Fi).
  * `view-distance: 6` or `8` (Let the CPU breathe. Keep view distance reasonable).
* **`paper-world-defaults.yml`:**
  * Reduce entity activation ranges for mobs (`entity-activation-range`) to avoid unnecessary server ticking.
  * Optimize hopper check frequencies to reduce tile entity lag significantly.

### 4. Securing Your Home Connection
Never share your actual home IP address on public forums or Reddit. 
* Avoid opening ports (Port Forwarding) on your home router if possible.
* Use reverse proxy tunneling systems like **Playit.gg** to mask your location and absorb potential DDoS attacks automatically.

---

## 💬 Support & Contribution

Feel free to open an issue if you encounter any performance bottlenecks in 1.21.11! 

If you found these optimization guidelines helpful, please consider giving this repository a ⭐ **Star** and checking out the pre-configured [1-Click Pack](https://nobrainbacon.gumroad.com/l/lsipw) to support independent developers!
