
<p align="center">
  <img src="https://github.com/user-attachments/assets/2d1f9f7a-411d-4d14-a11e-8b73fecb7192" alt="Driver Booster Pro logo" width="96" />
</p>

<h1 align="center">Driver Booster Pro</h1>

<p align="center">
  <em>Automatic driver updates for Windows — scan, verify, install, roll back. <br>Built for people who'd rather not think about drivers until something breaks.</em>
</p>

<p align="center">
  <a href="#"><img src="https://github.com/user-attachments/assets/2fa69fb4-7164-4e99-b1b8-e269a203c3d1" alt="Latest build" /></a>
</p>

---

<table>
<tr>
<td width="55%" valign="top">

### What Driver Booster Pro is

Driver Booster Pro is a Windows utility that keeps the drivers on your PC current. It scans your hardware, compares what's installed against a catalog of official driver releases, and installs newer versions when they exist — with a backup written before anything changes.

If you've ever opened Device Manager to a yellow warning triangle, or spent an evening hunting for the right GPU driver on a manufacturer's site, this tool exists to remove that evening from your life.

</td>
<td width="45%" valign="top">
<br>
<img src="https://github.com/user-attachments/assets/452ce422-4550-4cc8-8783-7887b78c7474" alt="Driver Booster Pro main window showing scan results" width="100%" />


</td>
</tr>
</table>

---

### How it works, in plain terms

Most driver tools either automate too aggressively — installing whatever they find without checking — or leave you to manually match version numbers against a manufacturer's download page. Driver Booster Pro sits in the middle: it automates the tedious parts (finding, downloading, verifying) while keeping you in control of what actually gets installed.

**Scanning.** The tool reads device IDs, current driver versions, and install dates from your system. Nothing is downloaded during a scan.

**Matching.** Each detected driver is compared against a curated catalog of official releases. Entries are sourced from manufacturer publications — no repacks, no third-party mirrors, no "optimized" builds from unknown sources.

**Backing up.** Before installation begins, the existing driver is copied to a backup folder you control. This is the part that makes the whole thing safe to use: if a new driver causes problems, restoring the old one takes one click.

**Installing.** The new driver is installed using standard Windows driver installation. Some drivers require a reboot to take effect — the tool will tell you when.

**Scheduling.** Scans can run daily, weekly, or only when you trigger them manually. For machines that need to stay current without supervision, silent install mode skips the prompts.

---

<table>
<tr>
<td width="45%" valign="top">
<br>
<br>
<br>
<br>
<br>
<br>
<img src="https://github.com/user-attachments/assets/3ac20d60-2c62-48e9-a1f3-004a51a5481c" alt="Driver Booster Pro backup and restore panel" width="100%" />


</td>
<td width="55%" valign="top">

### What you get beyond the basics

**Backup and restore that actually works.** Not a checkbox that writes a file somewhere you'll never find — backups go to a folder you choose, with a restore button in the UI.

**Offline packages.** For machines that don't touch the internet, download the package elsewhere and carry it over. The tool installs from the local package the same way it would from the network.

**Silent mode for unattended machines.** Useful for small offices or family PCs you maintain remotely — installs proceed without prompts, logs record what happened.

**Detailed logs.** Every scan, download, and install is logged. When something fails, the log tells you which step and why, instead of a generic "update failed" dialog.

**Scheduled scans that don't interrupt.** The scheduler respects fullscreen applications — no popups mid-game or mid-presentation.

</td>
</tr>
</table>

---

### Which Windows versions it supports

Driver Booster Pro supports Windows 7 SP1 through Windows 11, including Server editions from 2016 onward. Windows on ARM is partially supported — some drivers simply aren't published for ARM yet, and the tool will tell you when a driver has no ARM equivalent rather than installing something incompatible.

If you're on Windows 7 SP1 or 8.1, note that Microsoft has ended mainstream support for both, and some manufacturers have stopped publishing new drivers. The tool will still work with what's available, but "latest available" may not mean "recently updated."

---

### Installing and running it for the first time

The first run matters more than subsequent ones, because it's when you establish the backup habit. Here's the sequence that works best:

1. **Download the latest build** from Releases and run the installer.
2. **Launch as Administrator** — driver installation requires elevation, and the tool will refuse to install without it.
3. **Create a Windows restore point** before your first bulk update. This is separate from the tool's own backup and covers cases the tool can't (like a driver that destabilizes the OS before the tool can restore).
4. **Run a scan.** Review what it finds before clicking update.
5. **Update in batches if you're cautious** — GPU and chipset drivers first, then the rest.
6. **Reboot when prompted.** Some drivers only take effect after a restart.
7. **Set a scan schedule** in settings so future updates happen without you thinking about them.

---

### Settings that change behavior

The defaults work for most people, but a few settings are worth knowing about:

- **`scan.schedule`** — daily, weekly, or manual. Weekly is a reasonable default for a personal machine.
- **`backup.enabled`** — leave this on unless you have a specific reason to disable it.
- **`backup.location`** — point this at a drive with space. Driver backups aren't large, but they accumulate.
- **`update.offline`** — switch to offline mode when the target machine has no internet access.
- **`update.silent`** — installs without prompts. Useful for unattended machines, risky for machines you're actively using.
- **`log.level`** — bump to `debug` when troubleshooting, drop back to `info` afterward.

---

### Common questions, answered directly

**Is this the paid Pro version?**
Yes. Licensing details are on the official site. This repository is where releases and documentation live, not the storefront.

**Will it install drivers from unofficial sources?**
No. The catalog contains only official releases. If a driver isn't in the catalog, it won't be offered.

**What happens if a new driver breaks something?**
Restore the backup. The previous driver is in the backup folder, and the UI has a restore button that puts it back.

**Can I use it without an internet connection?**
Yes, with offline packages. Online updates require a connection.

**Does it work on Windows on ARM?**
Partially. Some drivers aren't published for ARM. The tool will indicate when a driver has no ARM equivalent.

**Can I update all drivers at once?**
Yes, but create a restore point first. Bulk updates are convenient, not risk-free.

**Where are backups stored?**
In the folder set by `backup.location`. The default is the app's own backup directory.

---

### When an update doesn't go as planned

| Symptom | Likely cause | First step |
| :--- | :--- | :--- |
| Scan returns no results | Network issue or stale catalog | Check connection, refresh catalog in settings |
| Install fails partway | Insufficient permissions | Run as Administrator, check log tail |
| PC unstable after update | Incompatible driver version | Restore previous driver from backup folder |
| Offline package rejected | Package doesn't match Windows build | Verify package matches your OS version and architecture |
| App won't launch | Missing .NET runtime | Install required runtime, try elevated launch |
| Backup folder missing | Folder deleted or moved | Recreate folder or repoint `backup.location` |

---

### Contributing

Bug reports, catalog corrections, and documentation fixes are welcome. When opening a pull request, include a clear description of what changed and why. When reporting a bug, attach the relevant log section — it shortens debugging considerably.

---

### Legal and practical notes

Driver Booster Pro is maintained by the Driver Booster Pro team and installs only official driver releases from a verified catalog. You are responsible for creating backups and restore points before updating, and for complying with the laws in your jurisdiction. Driver updates can affect system stability — the backup and restore features exist for exactly this reason, and using them is not optional if you value your time.

---

<p align="center">
  <sub>driver booster pro · automatic driver updater for windows · driver backup and restore · offline driver updates · scheduled driver scans · official driver catalog · windows 11 drivers · windows 10 drivers · windows 7 drivers · gpu driver update · chipset driver update · silent driver install · driver rollback · driver diagnostics · pc performance optimization · windows utility · hardware compatibility · driver database</sub>
</p>
