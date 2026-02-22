# User Backup Guide (user_backup.sh)

This script provides a simple backup mechanism for your folders.  
You use it via the command: **`user_backup.sh`**.

### Important note 1

**You should only backup folders from within your home directories on servers. Paths from `/mnt/unitymatrix/` and `/mnt/storage/` indicated by your PI will be backed up using another mechanism - please contact your PI**

### Important note 2

**Backup has to be enabled for each server separately**

### Important note 3

**By default each user get 1 TB of backup space. It's assumed that even if you keep large datasets in your home for convenience, these data sit also on `/mnt/unitymatrix/` or `/mnt/backups` and will be caked up by the mechanism signalled above.**

=========================================================================

How the backup works:
- your backup is stored under **`/mnt/backups/<your_login>/<server_name>/data/...`**
- it is a **mirror** backup: if you delete something in the source, it will also be removed from the backup on the next run
- backups are usually executed automatically at night, but you can run them manually anytime

---

## 1) Most important commands

### Show help
```bash
user_backup.sh help
```

### Show status
```bash
user_backup.sh status
```

### Enable backups on this server (run once)
```bash
user_backup.sh enable
```

### Add a folder to back up
```bash
user_backup.sh add /absolute/path/to/folder
```

### Add a folder with exclusions
```bash
user_backup.sh add /absolute/path -exclude .git -exclude node_modules
```

### List configured entries
```bash
user_backup.sh list
```

### Run backup manually
```bash
user_backup.sh run
```

### Remove an entry (it will no longer be backed up)
```bash
user_backup.sh remove /absolute/path
```

### Disable backups on this server (does not delete existing backup data)
```bash
user_backup.sh disable
```

---

## 2) First-time setup (recommended)

1. Enable backup:
```bash
user_backup.sh enable
```

2. Add a folder you want to protect (example):
```bash
user_backup.sh add /home/<your_login>/important
```

3. Add exclusions if needed:
```bash
user_backup.sh add /home/<your_login>/projects -exclude .git -exclude node_modules -exclude "**/.cache/**"
```

4. Verify your list:
```bash
user_backup.sh list
```

5. Run a manual test backup:
```bash
user_backup.sh run
```

---

## 3) Where the configuration is stored

Your list of folders is stored in:

```text
~/.config/user_backup/paths.list
```

You can edit it manually (for example with `nano`):

```bash
nano ~/.config/user_backup/paths.list
```

### `paths.list` format
Each non-empty, non-comment line contains:
- an absolute folder path
- optional exclusions: `-exclude PATTERN`

Example:

```text
/home/<your_login>/important
/home/<your_login>/projects -exclude .git -exclude node_modules -exclude "**/.cache/**"
```

Lines starting with `#` are comments and are ignored.

---

## 4) Exclusions (-exclude) explained

`-exclude` skips files/folders **inside** the selected source folder.

Examples:
- `-exclude .git` → skips the `.git` folder
- `-exclude node_modules` → skips `node_modules`
- `-exclude "*.tmp"` → skips `.tmp` files
- `-exclude "**/.cache/**"` → skips `.cache` folders anywhere under the source tree

If a pattern contains spaces, put it in quotes:
```bash
user_backup.sh add /home/<your_login>/data -exclude "My Folder"
```

---

## 5) What happens after `remove`

Command:
```bash
user_backup.sh remove /path
```

- removes the entry from your configuration
- **does not delete** existing backup data stored under `/mnt/backups/...`

Old backup data remains until you delete it manually.

---

## 6) Important rules / limitations

### A) Folders only (not single files)
Entries must point to directories.

### B) This is a mirror backup
The script uses `rsync --delete`, which means:
- the backup reflects the current state of the source folder
- deleted files will also be deleted from the backup on the next run

### C) Permissions under `/mnt/backups`
Your folders under `/mnt/backups/<your_login>/...` are created as **owner-only** (private).  
Other users should not be able to access them.

---

## 7) Common issues

### “command not found”
Try:
```bash
/usr/local/bin/user_backup.sh help
```

### “Backup root /mnt/backups does not exist” or permission errors
- most commonly `/mnt/backups` is not available on this server

### Backup “does nothing”
- verify you have entries in `paths.list`:
```bash
user_backup.sh list
```
- check that backup is enabled:
```bash
user_backup.sh status
```

---

## 8) Quick cheat sheet (TL;DR)

```bash
user_backup.sh enable
user_backup.sh add /home/<login>/important -exclude .git -exclude node_modules
user_backup.sh run
user_backup.sh status
```
