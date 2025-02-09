# Week 2: Linux System Administration & Automation


## 🚀 Project: DevOps Linux Server Monitoring & Automation
Imagine you're managing a **Linux-based production server** and need to ensure that **users, logs, and processes** are well-managed. You will perform real-world tasks such as **log analysis, volume management, and automation** to enhance your DevOps skills.

---

## 📌 Tasks

### **1️⃣ User & Group Management**
- Learn about Linux **users, groups, and permissions** (`/etc/passwd`, `/etc/group`).
- **Task:**  
  - Create a user `devops_user` and add them to a group `devops_team`.
  - Set a password and grant **sudo** access.
  - Restrict SSH login for certain users in `/etc/ssh/sshd_config`.

SOLUTION:

sudo useradd devops_user
sudo groupadd devops_team
sudo usermod -aG devops_team devops_user 
sudo passwd devops_user 
New password: 
Retype new password: 
passwd: password updated successfully
sudo usermod -aG sudo devops_user 

sudo nano /etc/ssh/sshd_config
Add the following line:
DenyUsers restricted_user
Restart SSH service:
sudo systemctl restart sshd

---

### **2️⃣ File & Directory Permissions**
- **Task:**  
  - Create `/devops_workspace` and a file `project_notes.txt`.
  - Set permissions:
    - **Owner can edit**, **group can read**, **others have no access**.
  - Use `ls -l` to verify permissions.

SOLUTION:

mkdir /devops_workspace
cd ./devops_workspace
touch project_notes.txt

chmod 640 project_notes.txt

---

### **3️⃣ Log File Analysis with AWK, Grep & Sed**
Logs are crucial in DevOps! You’ll analyze logs using the **Linux_2k.log** file from **LogHub** ([GitHub Repo](https://github.com/logpai/loghub/blob/master/Linux/Linux_2k.log)).

- **Task:**  
  - **Download the log file** from the repository.
  - **Extract insights using commands:**
    - Use `grep` to find all occurrences of the word **"error"**.
    - Use `awk` to extract **timestamps and log levels**.
    - Use `sed` to replace all IP addresses with **[REDACTED]** for security.
  - **Bonus:** Find the most frequent log entry using `awk` or `sort | uniq -c | sort -nr | head -10`.
 
SOLUTION:

1. Download the log file:
   ```sh
   wget https://github.com/LogHub/Linux_2k.log
   ```
2. Extract insights:
   - Find all occurrences of "error":
     ```sh
     grep -i "error" Linux_2k.log
     ```
   - Extract timestamps and log levels:
     ```sh
     awk '{print $1, $2, $3}' Linux_2k.log
     ```
   - Replace all IP addresses with `[REDACTED]`:
     ```sh
     sed -E 's/[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+/[REDACTED]/g' Linux_2k.log
     ```
   - Find the most frequent log entry:
     ```sh
     awk '{print $0}' Linux_2k.log | sort | uniq -c | sort -nr | head -10
     ```
---

### **4️⃣ Volume Management & Disk Usage**
- **Task:**  
  - Create a directory `/mnt/devops_data`.
  - Mount a new volume (or loop device for local practice).
  - Verify using `df -h` and `mount | grep devops_data`.

---

### **5️⃣ Process Management & Monitoring**
- **Task:**  
  - Start a background process (`ping google.com > ping_test.log &`).
  - Use `ps`, `top`, and `htop` to monitor it.
  - Kill the process and verify it's gone.
    
SOLUTION:
1. Start a background process:
   ```sh
   ping google.com > ping_test.log &
   ```
2. Monitor it using:
   ```sh
   ps aux | grep ping
   top
   htop
   ```
3. Kill the process:
   ```sh
   pkill ping
   ```
4. Verify it's gone:
   ```sh
   ps aux | grep ping
---

### **6️⃣ Automate Backups with Shell Scripting**
- **Task:**  
  - Write a shell script to back up `/devops_workspace` as `backup_$(date +%F).tar.gz`.
  - Save it in `/backups` and schedule it using `cron`.
  - Make the script display a success message in **green text** using `echo -e`.

SOLUTION

#!/bin/bash

# Define variables
SOURCE_DIR="/devops_workspace"
BACKUP_DIR="/backups"
BACKUP_FILE="backup_$(date +%F).tar.gz"

# Ensure backup directory exists
mkdir -p "$BACKUP_DIR"

# Create the backup
tar -czf "$BACKUP_DIR/$BACKUP_FILE" "$SOURCE_DIR"

# Check if the backup was successful
if [ $? -eq 0 ]; then
    echo -e "Backup successful: $BACKUP_DIR/$BACKUP_FILE"
else
    echo -e "Backup failed!"
fi

CRON:

0 2 * * * /path/to/backup.sh >> /var/log/backup.log 2>&1


---

## 🎯 Bonus Tasks (Optional 🚀)
1. Find the **top 5 most common log messages** in `Linux_2k.log` using `awk` and `sort`.
2. Use `find` to list **all files modified in the last 7 days**.
3. Write a script that extracts and displays only **ERROR and WARNING logs** from `Linux_2k.log`.

---

## 📢 How to Submit
- **Write a LinkedIn post** summarizing your Week 2 experience.
- Include screenshots or logs of your tasks.
- **Use hashtags**: `#90DaysOfDevOps` `#LinuxAdmin` `#DevOps`
- Share any blog posts, GitHub repos, or articles you create.

---

## 📚 Resources to Get Started
- [Linux In One Shot](https://youtu.be/e01GGTKmtpc?si=FSVNFRwdNC0NZeba)
- [Linux_2k.log (LogHub)](https://github.com/logpai/loghub/blob/master/Linux/Linux_2k.log)

---

## 📝 Example Submission Post
```markdown
Week 2 of #90DaysOfDevOps2025 done! 🏆

✅ Managed users & SSH access  
✅ Set up permissions & volumes  
✅ Analyzed logs using AWK & grep  
✅ Automated backups with a shell script  

Check out my blog here: [Your Blog/GitHub Link]  

#Linux #SysAdmin #DevOps
```

---

Happy learning, and see you in **Week 3**! 🚀
