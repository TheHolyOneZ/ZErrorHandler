# ZErrorHandler
A friendly yet **powerful Discord bot error-handler** that keeps your server calm when commands misbehave. ZErrorHandler gives you **one clean control panel** to catch, log, and style every bot error—no code edits required.
> 💡 **Built for the Zygnal Ecosystem — to download and use this extension, you must be part of the Zygnal Ecosystem.**  
> This extension (cog) is part of the **Zygnal Ecosystem** and is only available through its supported platforms.  
> You can use it with:  
> - The **[Discord Bot Framework](https://github.com/TheHolyOneZ/discord-bot-framework)** — ideal for developers who want full control and flexibility *(includes an integrated extension marketplace)*, or  
> - The **[ZygnalBot](https://zygnalbot.de)** — a prebuilt, plug-and-play Discord bot *(also includes an integrated extension marketplace)*.  
>
> Browse and install extensions at [zygnalbot.com/extension](https://zygnalbot.com/extension).  
> For help or community discussions, join us on Discord: [discord.gg/sgZnXca5ts](https://discord.gg/sgZnXca5ts)
# Advanced ZErrorHandler

A friendly yet **powerful Discord bot error-handler** that keeps your server calm when commands misbehave.
Advanced ZErrorHandler gives you **one clean control panel** to catch, log, and style every bot error—no code edits required. Built for public, multi-guild bots, it ensures each server gets its own independent configuration and statistics.

---

## ✨ Key Features

* **Multi-Guild Ready** – Each server gets independent control and stats.
* **Per-Server Control Panel** – Configure everything live inside Discord with an intuitive UI.
* **Granular Access Control** – Admins have default access and can delegate panel permissions.
* **Live Error Log** – Auto-updating embed for real-time error summaries.
* **Whitelist System** – Ignore errors from specific users, roles, or channels.
* **Argument Handling** – Catches missing/invalid command arguments and responds with correct usage.
* **User Rate Limiting (Owner-Only)** – Prevent command spam across the bot.
* **Total Takeover (Optional)** – Override all other error handlers to catch everything.
* **Statistics Dashboard** – Live error counts, top errors, and exportable stats per server.
* **Owner Alerts** – Optionally DM the bot owner on server errors.
* **Auto-Cleanup** – Old errors auto-delete or auto-archive.

---

## 📚 Basic Commands

| Command      | Shortcuts                     | What it Does                                           |
| ------------ | ----------------------------- | ------------------------------------------------------ |
| `errorpanel` | `ep`, `errors`, `errorconfig` | Opens the interactive control panel for the server.    |
| `errorstats` | `es`                          | Shows live error counts, top errors, and current rate. |
| `errorclear` | `ec`                          | Wipes all stored error stats for the server.           |

*Owner-only means the user ID in the `BOT_OWNER_ID` environment variable.*

---

## 🕹️ Inside the Control Panel

The panel is an interactive embed with organized buttons and dropdowns for easy navigation.

### Main Buttons

* **🏠 Main** – Toggle the handler on/off and reset stats.
* **🔒 Permissions** – Customize missing-permission messages and auto-delete timing.
* **⏰ Cooldowns** – Configure cooldown messages, reactions vs text, and error rate-limit settings.
* **📝 Arguments** – Customize messages for bad or missing command arguments.
* **🛡️ Whitelist** – Manage users, roles, and channels to ignore.
* **🎨 Design** – Switch between embeds or plain text, pick colors, and edit templates.
* **🔑 Access** – Grant panel access to specific users or roles.
* **⚡ Rate Limit (Owner Only)** – Configure per-user command rate limit.
* **📄 Logging** – Console logs, server log channel, or owner DMs.
* **📊 Stats** – View and export detailed server error stats.
* **🔴 Live Log** – Auto-updating live error log embed.
* **📜 Credits** – View script info and credits.

### Quick Actions (Dropdown on Main Page)

* Export current JSON config.
* Reset server settings to defaults.
* Toggle auto-refresh.
* Open advanced settings modal.

### Extra Buttons

* **🔄 Refresh** – Manually refresh the panel.
* **⚙️ Advanced** – Enable “nuclear takeover,” suppress original errors, tweak rate-limit options.

---

## 🧩 Features at a Glance

* **Permission Handling**: Custom messages for missing permissions.
* **Cooldown Handling**: Reaction ping or message, with configurable delete timers.
* **Argument Handling**: Custom messages with placeholders like `{usage}` and `{param}`.
* **Command Not Found**: Friendly, configurable notices.
* **Live Design Editing**: Edit titles, descriptions, and placeholders like `{user}`, `{retry_after}`, or `{permissions}`.
* **Logging Flexibility**: Console output, dedicated channel embeds, or private owner DMs.
* **Full Customization**: Nearly every message, color, and timer is configurable.

---

## 🚀 Setup

1. Add the `ERROR_HANDLER.py` cog to your bot's cogs folder and load it.
2. Set the environment variable `BOT_OWNER_ID` to your Discord user ID (required for DM Owner and rate-limit panel).
3. Ensure your bot has permissions: Send Messages, Embed Links, Add Reactions, and Manage Messages (for auto-delete).
4. Run the bot and use `!errorpanel` (or your bot’s prefix) to open the dashboard.

No extra coding required.

---

**Advanced ZErrorHandler** keeps your bot professional and your users informed while giving server administrators instant, granular control over every kind of command error.



# Changelog: V1 vs. V2.0.1

This document outlines the major changes, new features, and architectural evolution from the original V1 script to the newer, multi-guild V2.0.1. The new script represents a complete architectural rewrite to support public bots, adding significant new functionality and improving usability, robustness, and maintainability.

---

## 💥 Major Architectural Changes

| Feature | V1 | V2.0.1 |
|---------|----|--------|
| Multi-Guild Architecture | Single global configuration (`self.config`). All settings applied to every server. | Multi-guild; configurations and stats stored per server (`self.guild_configs`, `self.guild_stats`). Supports server-specific settings. |
| Panel Access Control | Control panel (V1) was owner-only. | Server admins have default access; can grant access to specific users/roles via "Access" page. |

---

## ✨ New Features & Modules

| Feature | Description |
|---------|------------|
| 🛡️ Whitelist System | Specify users, roles, or channels to ignore errors. Useful for testing channels or trusted admins. |
| 🔴 Live Error Log | Real-time embed with server error summary (total errors, error rate, most common errors, recent incidents). Fully customizable. |
| ⚡ User Command Rate Limiting | Limits how many commands individual users can run in a set period. Bot-owner-controlled to prevent spam. |
| 📝 Argument Error Handling | Handles `MissingRequiredArgument` and `BadArgument` errors separately. Configurable messages in panel. |
| 📜 Credits Page | Displays attribution and version info. |

---

## GUI & UX Improvements (Control Panel)

| Feature | V1 | V2.0.1 |
|---------|----|--------|
| Panel Redesign | Basic layout. | Logical rows; new pages (Arguments, Whitelist, Access, Live Log, Rate Limit, Credits); context-aware buttons. |
| Live Previews | Minimal previews. | Full previews for all major error types; Whitelist/Access lists displayed. |
| Modals | Single ID add/remove. | Bulk entry with comma-separated values; separate fields for add/remove. |
| UI Complexity | Advanced settings exposed (error_cache_size, auto_cleanup). | Simplified; advanced settings handled internally. |

---

## ⚙️ Core Error Handling & Stability Improvements

| Feature | V1 | V2.0.1 |
|---------|----|--------|
| Configuration Backfilling | Not available. | Automatically fills missing configuration keys from defaults. |
| Patcher Logic | Aggressive patching of multiple discord.py layers. | Streamlined patching; ensures functions restored when cog is unloaded. |
| Duplicate Error Prevention | `_ultimate_handler_processed` flag. | `_global_handler_processed` flag; more reliable. |
| Message Formatting | `.format()` — may raise `KeyError`. | `.format_map(defaultdict(str, ...))` — missing variables replaced by empty strings. |
| Panel & Live Log Refresh | Minimal error handling. | Graceful handling of deleted messages; recreates or removes them. |

---

## ⚙️ Code & Backend Improvements

| Feature | V1 | V2.0.1 |
|---------|----|--------|
| Configuration & Stats | Single JSON file, stats in memory. | Single JSON stores all guild configs; stats stored per guild. |
| State Management | Standard lists/dictionaries. | Uses `collections.defaultdict` and `collections.deque` for efficiency. |
| Dependency Versioning | Strict version checks. | Flexible (checks major.minor only). |
| Codebase | Basic structure; less modular. | Refactored for readability and maintainability; guild-specific logic organized. |

