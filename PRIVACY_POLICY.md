# Privacy Policy for DeviceCare

**Effective date:** September 18, 2026
**Last updated:** September 18, 2026
**Developer:** crish29
**Contact:** crishcatalin@gmail.com

---

## The short version

- No account. No sign-up. No login.
- No analytics, no advertising, no crash reporting, no tracking of any kind.
- Everything DeviceCare reads about your device **stays on your device**.
- Exactly **one** thing ever leaves your phone: when you open the Network screen, the app asks
  `api.ipify.org` what your public IP address is. That request carries no identifier, no account,
  and no data about your device. The service necessarily sees the IP address the request comes
  from — that address *is* the value being looked up.
- We do not collect your data, because the app has nowhere to send it and no server to send it to.

---

## 1. What DeviceCare reads on your device

DeviceCare is a device-inspection tool. To show you information about your phone, it reads a lot of it.
None of the following is transmitted anywhere, logged remotely, or shared:

| What it reads | Why |
|---|---|
| List of installed apps, their sizes, versions, icons, install/update dates | The Apps, Storage and App Details screens |
| Which apps you have used and when | The Usage screen (needs Usage Access) |
| Files on shared storage — names, sizes, dates, types | Storage Analyzer, Junk Cleaner, duplicate and large-file detection |
| Photos, videos and audio file metadata | Media categories in Storage Analyzer and the Cleaner |
| Battery level, charging state, temperature, health, voltage | Battery screens |
| CPU, RAM, storage capacity, screen, sensors, build info | Home and System Info screens |
| Network connection state, Wi-Fi details, mobile network type (LTE/5G), data counters | Network and System → Network screens |

All of this is read on demand, used to draw the screen in front of you, and discarded or cached
locally. It is never uploaded.

## 2. What leaves your device

**One request, to one destination, under one condition.**

When the Network screen is open and the app needs to display your public IP address — and the
previously fetched value is more than 5 minutes old — DeviceCare sends a plain `GET` request to
`https://api.ipify.org`.

- **What is sent:** nothing. The request has no parameters, no body, no headers identifying you or
  your device, and no account. It is a bare request for the caller's own IP address.
- **What the third party sees:** your public IP address, which is unavoidably visible to any server
  you contact, and the fact that a request was made. `api.ipify.org` is operated by a third party
  and its handling of that request is governed by its own policy.
- **When it happens:** only while you have the Network screen open, and at most once every 5
  minutes. DeviceCare does **not** make this request at app launch, and does **not** make it in the
  background. If you never open the Network screen, the request is never made. If your phone is
  offline, it fails silently and the field shows a dash.
- **Timeouts:** 4 seconds connect, 4 seconds read.

That is the entire network activity of this app. There is no other outbound connection.

**Links and shares, opened by you.** DeviceCare can hand something to another app when you ask it
to: opening an app's Google Play listing (for example, after uninstalling), sharing a file, or
opening a file in a viewer. These leave the app only through the Android system share sheet or a
link, and they go to whichever app you pick. The app sends nothing about you to us, and receives
nothing back.

## 3. What DeviceCare never does

- No user accounts, no email collection, no registration.
- No analytics SDK, no crash-reporting SDK, no advertising SDK. The app declares no third-party
  tracking library of any kind.
- No collection of your app list, usage history, file list, or device identifiers.
- No transmission of any of the data in section 1 — to us or to anyone else.
- No selling, renting, or sharing of personal data. There is none to sell.
- No background service. DeviceCare has no component that runs when the app is closed.

## 4. Permissions, and why each one is needed

| Permission | Why DeviceCare asks for it |
|---|---|
| **All files access** (`MANAGE_EXTERNAL_STORAGE`) | Storage Analyzer and Junk Cleaner must see every file on shared storage to report what is using your space, find duplicates, and find leftovers. Without it, the app can only see a small subset. |
| **Read media** (`READ_MEDIA_IMAGES`, `READ_MEDIA_VIDEO`, `READ_MEDIA_AUDIO`) | The Photos / Videos / Audio categories, used on Android 13+. |
| **Read storage** (`READ_EXTERNAL_STORAGE`) | The same access on Android 12 and older. |
| **Query all packages** (`QUERY_ALL_PACKAGES`) | The Apps screen lists your installed apps. Android hides installed packages from apps by default; this permission is what allows the list to be complete. |
| **Usage access** (`PACKAGE_USAGE_STATS`) | Powers the Usage screen — which apps you open and how often. This is a special access you grant in system Settings, and DeviceCare can only read it, never alter it. |
| **Network state** (`ACCESS_NETWORK_STATE`, `ACCESS_WIFI_STATE`) | Showing connection type, Wi-Fi details, and whether you are online. |
| **Phone state** (`READ_PHONE_STATE`) | Reading the mobile network type (LTE / 5G) on the Network screen. Requested at runtime the first time you open it. |
| **Delete packages** (`REQUEST_DELETE_PACKAGES`) | Required since Android 8 for the system's uninstall dialog to appear. The app **cannot** uninstall anything itself — it only asks the system to show the confirmation dialog, and you decide. |
| **Internet** (`INTERNET`) | Solely the public-IP lookup in section 2. |

You can decline or revoke any of these in Android Settings. Screens that depend on a permission
will not function without it; the rest of the app will.

## 5. Files: what DeviceCare writes

- **It reads** files on shared storage to analyse them.
- **It writes only to its own private app storage** — the locations Android reserves for the app,
  which are not visible to other apps and are removed when you uninstall:
  - the **Recycle Bin**, where files you delete are kept so you can restore them;
  - extracted APKs, when you ask the app to extract an installed app's installation file;
  - a cached index of your file listing, and cached app icons, so screens open faster.
- **It deletes** a file only when you explicitly tell it to, and only after a confirmation dialog.
  Deleted files go to the Recycle Bin first, not to oblivion, unless you choose to delete them
  permanently.
- **It never modifies** the contents of your files.

## 6. Retention and your control

DeviceCare stores nothing on any server, so there is no server-side data to retain or delete.

On your device:

- **Uninstalling DeviceCare removes everything** it stored — caches, index, settings, and the Recycle
  Bin.
- **Settings → Clear Icon Cache** clears the cached app icons immediately.
- **The Recycle Bin** holds deleted files until you empty it or delete them permanently.

**Android backup.** DeviceCare sets `android:allowBackup="true"`, which means Android's own backup
system may include the app's settings and data in a device backup tied to *your* Google account,
if you have device backup enabled. That backup is between you and Google; the developer of DeviceCare
has no access to it. You can disable it in Android Settings → System → Backup.

## 7. Children

DeviceCare is a utility app and is not directed at children. It collects no personal information from
anyone, including children under 13.

## 8. Changes to this policy

If this policy changes, the "Last updated" date above will change with it. Material changes — for
example, if the app ever begins sending data somewhere — will be noted in the app's release notes
on Google Play.

## 9. Contact

Questions about this policy or about privacy in DeviceCare:

**crishcatalin@gmail.com**

---

*This policy describes DeviceCare as published on Google Play. It is written to match what the
application actually does, and it is intended to be read alongside the Data safety declaration on
the app's Play Store listing.*
