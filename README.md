# QYRYX

**A simple, safe control panel for your home server.** Manage your Ubuntu server from a web page instead of typing commands.

QYRYX is for people who run a server at home: an old laptop, a mini PC or a Raspberry Pi. You can install apps, put your own projects online, keep everything updated and see whether anything is wrong. Everything is done with buttons and plain-language explanations.

You don't have to memorise commands, and nothing happens behind your back. QYRYX shows you a plan, waits for your OK, does the work, and then **checks that it actually worked**.

---

## Why use QYRYX instead of the command line?

The command line is powerful, but it's easy to get wrong. A typo can break things, error messages are cryptic, and nothing stops you from running something harmful. QYRYX gives you the same control with a safety net.

| On the command line | In QYRYX |
|---|---|
| You need to know the exact command | You click what you want, or type it into the search bar in plain words |
| Commands run immediately, with no preview | You see a plan of every step first, and nothing happens until you approve it |
| You have to check yourself whether it worked | QYRYX checks the result and marks it **verified**, or tells you what went wrong |
| When an update breaks something, you fix it by hand | QYRYX puts the previous working version back automatically |
| Error messages look like `exit status 1` | Errors are explained in plain language, with what to do next |
| You can delete something important by accident | Deleted files go to a recycle bin, and QYRYX refuses anything that would break Ubuntu |
| You have to remember what you changed and when | Every change is kept in a history with its steps and result |
| You only notice a security problem if you go looking | Guardian checks the server every 6 hours and explains anything it finds |

You don't lose the command line, either. You can still use SSH whenever you like. QYRYX also has an optional built-in terminal, which is off by default and protected by your password.

---

## Deploying your apps: from your computer to running in a few clicks

Getting your own project running on a server usually means copying files, setting up environments, writing service files and hoping nothing breaks. QYRYX turns this into a short, guided process with automatic switch-back if something fails.

**Your own project (Python, Flask, FastAPI):**

1. **Upload** your project folder: drag it from your computer onto the Files page.
2. **Pick it** under Deployments → New deployment. QYRYX looks inside and suggests how to run it. For example, it recognises a Flask app with `app.py` and `requirements.txt`.
3. **Confirm.** QYRYX copies it into a new numbered release, sets up its Python environment, starts it as a service that restarts on reboot, and checks that it answers.

**To update:** upload the new version and click **Update**. If the new version doesn't start, QYRYX switches back to the previous one by itself. Your app's saved data is kept separately, so it carries over from one release to the next.

**Ready-made apps: the Application Library.** Install popular self-hosted apps with one click. Each one is hand-picked and checked, and QYRYX shows the memory, storage and ports it needs before you install it.

- **Media and files:** Jellyfin, Syncthing
- **Productivity:** Paperless-ngx, Memos, Linkding
- **Monitoring:** Uptime Kuma, ntfy
- **Development and AI:** Gitea, Open WebUI
- **Tools:** Node.js, git, FFmpeg, htop, tmux and more
- **Guides:** step-by-step Tailscale setup

Uninstalling removes the app completely. Its data is kept unless you choose to erase it, so a reinstall picks up where you left off.

**Any other Docker app.** Paste a `docker-compose.yml` file or a `docker run` command. QYRYX converts it and checks it for risky settings, such as full administrator access or access to Docker itself. Then it installs the app and confirms it's running.

**Docker updates with an undo.** Updating a container downloads the new version, keeps your settings and data, and checks that it keeps running. If the new version fails, the old one comes back automatically.

---

## Everything QYRYX does

**Home and overview**
- See the server's health at a glance: processor, memory, storage, temperature, and which apps are up.
- A **System map** shows which apps can be reached, and from where: this server only, your home network, or your Tailscale devices.
- A **search bar** finds any page, app, setting or help article, and can start common actions.

**Applications**
- See every app on the server in one list: services, Docker containers and Compose projects.
- Start, stop or restart an app, and read its log.
- Add apps you already have, or uninstall them cleanly. A backup copy is kept, so you can bring one back.

**Docker**
- Containers, images, volumes and networks, explained.
- Run Docker Compose projects, with a risk check before anything starts.
- Updates with automatic rollback, and cleanup that never deletes your data volumes.

**Files**
- A file manager for your own folders, like Windows Explorer: upload, download, rename, move and delete.
- Browse the whole server read-only. Secret files such as passwords and keys are always hidden.
- Removing files outside your folders goes through a check that refuses anything that would break Ubuntu or QYRYX. Removed files go to a recycle bin first, so you can restore them.

**Automation**
- Simple rules, such as "restart this app if it stops" or "warn me when storage is low, the server is too hot, Docker stops or the internet goes down".
- Make your own buttons for things you do often.
- Run your own scripts safely: QYRYX shows you the script to review and approve, then runs it in a protected sandbox.
- A notification bell lists everything that needs your attention.

**Guardian (health and security checks)**
- Every 6 hours, Guardian checks for missing updates, failed services, firewall gaps, open ports, SSH settings, failed sign-ins, storage, temperature, file permissions, changes to who can sign in or act as administrator, old Docker images, missing backups and more.
- Each finding explains what was found, why it matters and what to do about it.

**System**
- **Ubuntu updates:** install all of them or only the ones you pick, and restart when needed.
- **Firewall:** for each open port, choose who should reach it: your home network and Tailscale, or Tailscale only. A change is tried first and undone automatically unless you can still reach QYRYX afterwards. QYRYX can also make Docker apps follow the firewall, which Docker normally bypasses.
- **Wi-Fi:** connect, switch networks or reconnect. If a change cuts the connection, QYRYX automatically goes back to the network that worked.
- **Backups (optional, off by default):** QYRYX finds attached drives and makes scheduled, encrypted backups of your app data. It never formats a drive.
- **Storage and cleanup:** see what's using space, free it up safely, and uninstall unused services. A copy is kept, so you can restore them.
- **Power:** restart the server. On laptops, you can also choose what happens when the lid is closed.
- **Command line:** an optional terminal in the browser, off by default. Turning it on needs your QYRYX password, and the terminal itself asks for your Ubuntu sign-in. It switches off after you've been idle for a while.

**History and help**
- **Activity:** every action you approve is kept with its steps and result.
- **Help:** a searchable guide with step-by-step instructions for everything above.

**Open it from anywhere: privately**
- In a browser on your PC or phone, at home or away, through **Tailscale**. Only your own devices can connect, and nothing is put on the public internet.
- On the server's own screen, if one is connected: QYRYX can run full-screen when the server starts.

**Keeps itself up to date**
- QYRYX checks for new versions and shows you what's new. Every update is checked against QYRYX's signature before it's installed, and if a new version doesn't start, the previous one is put back automatically.

---

## Safe by design

- **Nothing happens without your approval.** Every change shows a plan first.
- **Very little runs as administrator.** Only one small helper program has administrator rights, and it can only do a fixed list of checked tasks. The rest of QYRYX runs as a limited user.
- **QYRYX never does these on its own:** delete your data, change your firewall or network, restart the server as a "repair", or show passwords and keys.
- **Private by default.** QYRYX only answers on the server itself. You decide whether to open it to your own devices through Tailscale.
- **Signed downloads.** The installer and the updater refuse any file that isn't signed with QYRYX's release key.
- **Nothing is hidden.** The installation guide lists every user, program, service and folder QYRYX adds, and the uninstaller removes them all without touching your apps or data.

---

## What you need

- **Ubuntu 24.04 LTS or newer** (Server or Desktop), 64-bit
- A **64-bit Intel/AMD** computer (PC, laptop, mini PC) or a **64-bit ARM** board such as a Raspberry Pi 4 or 5
- **2 GB of memory** (4 GB or more if you run Docker apps) and **20 GB** of free storage
- Optional: **Docker** (for apps), **Tailscale** (for access from anywhere), **NetworkManager** (for Wi-Fi changes)

QYRYX itself is light: about 45 MB of memory and almost no processor use when idle.

---

## Install

On your Ubuntu server, run:

```
curl -fsSL https://github.com/JakeWill1/Qyryx/releases/latest/download/get.sh | sudo bash
```

The installer:

1. picks the right version for your processor;
2. checks that the download is genuine (signed with QYRYX's release key);
3. asks before changing anything;
4. shows a **one-time setup code** at the end.

Then open QYRYX in a browser, enter the code and create your account.

Prefer to read the script before running it? Download `get.sh` from the [latest release](https://github.com/JakeWill1/Qyryx/releases/latest), look through it, then run `sudo bash get.sh`.

**To open QYRYX from your other devices,** turn on the private Tailscale link. Run this in the installer folder (the installer shows the full path at the end):

```
sudo ./enable-remote-link.sh
```

**To remove QYRYX,** run `sudo ./uninstall.sh` from the same folder. Your apps, containers, files and data are not touched.

---

## Good to know

- QYRYX is **new**. It has been used every day on a real home server running Ubuntu 26.04. Other Ubuntu versions and ARM boards are supported, but they have been tested less.
- QYRYX **doesn't replace backups.** Turn on the optional backups, or use your own.
- "Looks fine" in Guardian means nothing was found. It's not a guarantee of safety.
- This repository contains the signed release files and the installer.
