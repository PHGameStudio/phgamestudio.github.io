---
layout: default
title: Antigravity SetUp Tutorial
permalink: /resources/antigravity-set-up-tutorial/
---

# Antigravity Setup Tutorial

---

## 1. Download

Antigravity can be downloaded from [www.antigravity.google](https://www.antigravity.google).

This is an AI IDE similar to windsurf but with more powerful **Vibe Coding and Agentic Ability**, so all settings on windsurf can be applied to antigravity.

## 2. Account Requirement

1. You need to have a **Google account** to use Antigravity.

2. this account must be at least 18 years old. (if your account is verified under 18, try to sign another one)

3. go to https://policies.google.com/terms and check the location of your account.\
If it's in **China mainland, Hong Kong, Macao**, your account is **Not Available**, and we suggest you to **create a new account** instead of changing location.(China Taiwan is available)

## 3. Environment requirement

1. you need a VPN with node in **outside of China mainland, Hongkong, Macao**

1. Either Rules or Global can open Antigravity. But **MUST open TUN mode in your VPN**. If you couldn't find, try another VPN container such as **ClashX Meta** on mac.
	- On windows, use [Clash Nyanpasu](https://github.com/libnyanpasu/clash-nyanpasu/), install its "service mode", start the service, and enable TUN mode. After that you don't need to configure proxy settings.
	- On linux it's recommended to install clash-meta (in some distros it's called `mihomo`), and run the setup script of [clashtui](https://github.com/JohanChane/clashtui). Some file ownerships might still need to be changed. After setup, enable the `clashtui_mihomo.service` service, import remote configs using the `clashtui` command, and access the dashboard at [http://localhost:9090/ui](http://localhost:9090/ui)
2. check if your **DNS is enabled**. This is **CRUTIAL** for Antigravity to work. If not and you don't know how, ask your ~~chatGPT~~claude or gemini to help you.

## 4. Model selection

Gemini 3 for frontend task

Claude sonnet 4.5 for backend task
