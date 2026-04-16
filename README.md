# Tether

A simple, structure-aware Google Drive sync engine for Obsidian, developed by **Llewellyn Paintsil**. Tether provides a seamless way to keep your entire vault—including settings, themes, and complex folder hierarchies—perfectly synced between your local device (Android/Desktop) and Google Drive using your own Google Cloud project so you control your data.

## 🌟 Key Features

### 📱 Full Android & Desktop Compatibility

Built specifically to bypass the limitations of mobile devices. Tether uses Obsidian's native `requestUrl` API to handle large network requests and file operations without triggering CORS errors or memory crashes on Android.

### 📁 Exhaustive Vault Structure Sync

- **Hidden Folders:** Syncs the `.obsidian` folder, ensuring your plugins, themes, hotkeys, and CSS snippets are identical across all devices.
- **Deep Nesting:** Supports vaults with complex sub-folder structures.
- **Vault Root Isolation:** Creates a dedicated folder named after your vault inside your chosen Google Drive directory.

### 🚀 Performance & Reliability

- **Resumable Uploads:** Uses Google's resumable upload protocol to handle files of any size with zero file size limits.
- **Auto-Pagination:** Correctly handles large vaults by automatically paginating through Google Drive API results.
- **Background Sync:** Automatically checks for updates on startup and at configurable intervals.

### 🛡️ Data Safety & Conflict Resolution

- **Keep Both Strategy:** If a file is edited on two devices simultaneously, Tether creates a `(conflict - timestamp)` copy. It **never** overwrites your local data during a conflict.
- **Mirror Deletions:** If you delete a file locally, it is automatically removed from Google Drive on the next sync.
- **Conflict Management:** View and open conflicted files directly from the sync sidebar to resolve them manually.

---

## 🛠️ Installation

1.  **Locate Plugin Folder:** Open your vault folder and navigate to `.obsidian/plugins/`.
2.  **Create Directory:** Create a folder named `tether-google-drive-sync`.
3.  **Transfer Files:** Copy the following 3 files from this project into that new folder:
    - `main.js`
    - `manifest.json`
    - `styles.css`
4.  **Enable Plugin:** Open Obsidian, go to `Settings > Community Plugins`, click the Refresh icon, and toggle **Tether** to ON.

---

## 🚀 Step-by-Step Setup Guide

Tether includes a **Setup Wizard** in the settings tab to guide you through these steps:

### Step 1: Create Google Cloud Credentials (Google Cloud Console)

1.  Go to [Google Cloud Console](https://console.cloud.google.com/)

<img src="images/step-1.png" align="center">

2.  Click **"Select a project"**

<img src="images/step-2.png" align="center">

3.  Click **"New project"**

<img src="images/step-3.png" align="center">

4.  In the project name field, type **"Tether-Sync"**

<img src="images/step-4.png" align="center">

5.  Click **"Create"** button.

<img src="images/step-5.png" align="center">

6.  Click **"APIs & Services"**

<img src="images/step-6.png" align="center">

7.  Click **"Library"**

<img src="images/step-7.png" align="center">

8.  Click the **"Search for APIs & Services"** field.

<img src="images/step-8.png" align="center">

9.  Type **"Google drive"**

<img src="images/step-9.png" align="center">

10. Click **"google drive api"**

<img src="images/step-10.png" align="center">

11. Click **"Google Drive API"**

<img src="images/step-11.png" align="center">

12. Click **"Enable"**

<img src="images/step-12.png" align="center">

13. Click **"OAuth consent screen"**

<img src="images/step-13.png" align="center">

14. Click **"Get started"**

<img src="images/step-14.png" align="center">

15. Click the **"App name"** field.

<img src="images/step-15.png" align="center">

16. Type **"Tether-Sync"**

<img src="images/step-16.png" align="center">

17. Click **User Support email**.

<img src="images/step-17.png" align="center">

18. Click **"your-email@gmail.com"**

<img src="images/step-18.png" align="center">

19. Click **"Next"**

<img src="images/step-19.png" align="center">

20. Click **"External"**

<img src="images/step-20.png" align="center">

21. Click **"Next"**

<img src="images/step-21.png" align="center">

22. Click **"Email addresses"** (Developer contact info)

<img src="images/step-22.png" align="center">

23. Click **"Next"**

<img src="images/step-23.png" align="center">

24. Click the **"I agree to the Google API Services: User Data Policy."** field.

<img src="images/step-24.png" align="center">

25. Click **"Continue"**

<img src="images/step-25.png" align="center">

26. Click **"Create"**

<img src="images/step-26.png" align="center">

27. Click **"Data Access"**

<img src="images/step-27.png" align="center">

28. Click **"Add or remove scopes"**

<img src="images/step-28.png" align="center">

29. Click the scope string: `https://www.googleapis.com/auth/drive https://www.googleapis.com/auth/drive.metadata.readonly openid email`

<img src="images/step-29.png" align="center">

30. Press **Ctrl + C** to copy it.

<img src="images/step-30.png" align="center">

31. Click the **"Manually add scopes"** field.

<img src="images/step-31.png" align="center">

32. Press **Ctrl + V** to paste the string.

<img src="images/step-32.png" align="center">

33. Click **"Add to table"**

<img src="images/step-33.png" align="center">

34. Click **"Update"**

<img src="images/step-34.png" align="center">

35. Click **"Save"**

<img src="images/step-35.png" align="center">

36. Click **"Audience"**

<img src="images/step-36.png" align="center">

37. Click **"Add users"**

<img src="images/step-37.png" align="center">

38. Click the field to add your email.

<img src="images/step-38.png" align="center">

39. Click **"Save"**

<img src="images/step-39.png" align="center">

40. Click **"Clients"**

<img src="images/step-40.png" align="center">

41. Click **"Create client"**

<img src="images/step-41.png" align="center">

42. Click the **"Application type"** dropdown.

<img src="images/step-42.png" align="center">

43. Click **"Web application"**

<img src="images/step-43.png" align="center">

44. Click the **"Name"** field.

<img src="images/step-44.png" align="center">

45. Press **Ctrl + A** to select all.

<img src="images/step-45.png" align="center">

46. Type **"Tether Sync"**

<img src="images/step-46.png" align="center">

47. Click the redirect URI: `https://obsidian.md`

<img src="images/step-47.png" align="center">

48. Press **Ctrl + C** to copy it.

<img src="images/step-48.png" align="center">

49. Switch back to the **"Create OAuth client ID"** tab.

<img src="images/step-49.png" align="center">

50. Click the **"Add URI"** icon.

<img src="images/step-50.png" align="center">

51. Click the **"URIs 1"** field.

<img src="images/step-51.png" align="center">

52. Press **Ctrl + V** to paste the URI.

<img src="images/step-52.png" align="center">

53. Click **"Create"**

<img src="images/step-53.png" align="center">

54. Click the **"Copy Client ID"** icon.

<img src="images/step-54.png" align="center">

55. Click the **"Copy Client Secret"** icon.

<img src="images/step-55.png" align="center">

56. Click **"OK"** and paste these keys into Tether's settings.

<img src="images/step-56.png" align="center">

### Step 2: Authentication

1.  In Obsidian settings for Tether, click **"Open Login Page"**.
2.  Log in with your Google account.
3.  You will be redirected to `obsidian.md`. **Copy the entire URL** from your browser bar.
4.  Paste that URL into the **"Authorization Code"** box in Obsidian and click **Verify Code**.

### Step 3: Choose Folder

1.  Click **"Select Drive Folder"**.
2.  Browse your Google Drive hierarchy.
3.  Either select an existing folder or create a new one.
4.  Click **"Select This Folder"** to begin syncing.

---

## 🔗 Author

**Llewellyn Paintsil**

- GitHub: [@Llewellyn500](https://github.com/Llewellyn500)
- Project Repo: [Tether](https://github.com/Llewellyn500/tether)

## 📄 License

This project is licensed under the MIT License.
