# 📨 Block New Outlook Migration on Windows 11 (24H2 Update)

Microsoft is automatically migrating users from **Classic Outlook** to the **New Outlook** during the **24H2 update on Windows 11**.

Many users prefer the **Classic Outlook** interface and do not wish to switch. This guide explains how to **block the migration to the New Outlook** and continue using Classic Outlook on your Windows 11 machine.

---

## 📌 Why Block the New Outlook?

* Users are accustomed to the **Classic Outlook interface**.
* Migration happens **automatically** when upgrading from **Windows 11 23H2 → 24H2**.
* Prevents **accidental switch** via the "Try the New Outlook" toggle.

---

## 🔄 Switching Back to Classic Outlook

If you have already migrated:

1. Look for the **toggle button** inside Outlook to switch back to Classic Outlook.
2. If the toggle is missing:

   * Open **Settings → Apps → Installed Apps**.
   * Uninstall **New Outlook**.
   * Reinstall **Classic Outlook** from the [Microsoft Store](https://apps.microsoft.com).
   * Follow the registry instructions below to prevent future migration.

---

## ✅ Update Classic Outlook

Before making registry changes:

1. Open **Outlook Classic**.
2. Go to **File → Office Account → Update Options → Update Now**.
3. Install any updates and restart Outlook.

---

## 🛠️ Block New Outlook via Windows Registry

> ⚠️ **Important:** Back up your registry before making changes.

* Open **Registry Editor (regedit)**.
* Go to **File → Export**.
* Select **All** in Export Range, give it a name, and save it (preferably on an external drive).

---

### 1. Hide the "Try the New Outlook" Toggle

**Path:**

```
HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Outlook\Options\General
```

* Create a new **DWORD (32-bit) Value**.
* Name it:

  ```
  HideNewOutlookToggle
  ```
* Set its value to:

  ```
  1
  ```

This removes the toggle button and prevents accidental switching.

---

### 2. Stop Outlook from Using the New Version

**Path:**

```
HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Outlook\Preferences
```

* Create a new **DWORD (32-bit) Value**.

* Name it:

  ```
  UseNewOutlook
  ```

* Set its value to:

  ```
  0
  ```

* **0 = Classic Outlook**

* **1 = New Outlook**

---

### 3. Block Migration During Windows Update

**Path (create keys if missing):**

```
HKEY_CURRENT_USER\Software\Policies\Microsoft\Office\16.0\Outlook\Preferences
```

* Create a new **DWORD (32-bit) Value**.
* Name it:

  ```
  NewOutlookMigrationUserSetting
  ```
* Set its value to:

  ```
  0
  ```

This prevents automatic migration when updating from **23H2 → 24H2**.

---

## 🎯 Final Notes

* After applying these steps, you can **safely continue using Classic Outlook** on Windows 11.
* Always back up your registry before making changes.
* If anything goes wrong, restore the registry backup you saved earlier.

---

💡 With these registry tweaks, you can **block Microsoft’s forced migration** and keep your favorite Classic Outlook!

---
