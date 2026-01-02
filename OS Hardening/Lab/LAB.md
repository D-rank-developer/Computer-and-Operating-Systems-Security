# Linux Operating System Hardening Lab Report

## Introduction
This lab focuses on implementing various Linux operating system hardening techniques including password policies, system security configurations, and user/group management to reduce attack surfaces and enhance system security. The implementation follows security best practices and CIS (Center for Internet Security) benchmarks to create a more secure Linux environment.

---

## Task 1: Password Policies Configuration

### 1.1 Password Complexity Requirements

First, I installed the required PAM module for password quality checking:

![libpam-pwquality installation](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image4.png)

The configuration was modified in `/etc/security/pwquality.conf` to enforce strong password requirements:

![pwquality.conf editing](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image5.png)

The password complexity settings were configured as follows:
- Minimum password length: 13 characters
- At least one digit required
- At least one uppercase character required
- At least one lowercase character required

![Password complexity settings](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image6.png)

I verified the minimum password length setting:

![Verifying minlen setting](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image10.png)

### 1.2 Password Reuse Limitation

The PAM configuration was updated to prevent password reuse:

![PAM configuration editing](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image7.png)

The `/etc/pam.d/common-password` file was modified to remember the last 5 passwords:

![Password reuse configuration](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image11.png)

The updated PAM configuration ensures SHA-512 hashing algorithm is used:

![SHA-512 configuration](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image12.png)

### 1.4 Minimum Days Between Password Changes

I checked the current `PASS_MIN_DAYS` setting:

![Checking PASS_MIN_DAYS](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image13.png)

The `/etc/login.defs` file was edited to set the minimum days between password changes:

![Editing login.defs](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image14.png)

Original settings showed `PASS_MIN_DAYS` as 0:

![Original login.defs settings](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image15.png)

Updated settings configured `PASS_MIN_DAYS` to 1 and `PASS_MAX_DAYS` to 365:

![Updated login.defs settings](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image16.png)

---

## Task 2: Disable Alt+Ctrl+Del Reboot

The Ctrl+Alt+Del reboot function was successfully disabled to prevent unauthorized system restarts:

![Disabling Ctrl+Alt+Del](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/f0dc3f9277abdd972c773bc1adfd9f7f6962328c/OS%20Hardening/Lab/password_configuration/IMAGE01.png)

The command created a symlink to `/dev/null`, effectively masking the Ctrl+Alt+Del target.

---

## Task 3: Disable USB Storage

USB storage was disabled by blacklisting the usb-storage module:

![Editing blacklist.conf](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image18.png)

The blacklist configuration file was modified:

![Blacklist configuration](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image19.png)

---

## Task 4: System File Permission Hardening

### 4.1 /etc/passwd File Permissions

The permissions of `/etc/passwd` were verified:

![Checking /etc/passwd permissions](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image20.png)

The file shows appropriate permissions (0644) with root ownership, ensuring only authorized access.

Attempted to modify `/etc/passwd` permissions without proper privileges:

![Permission denied error](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image21.png)

Received operation not permitted error when trying to change permissions without sudo:

![Permission change failed](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image22.png)

### 4.2 Ensure Root is the Only UID 0 Account

Verified that only the root account has UID 0:

![Checking UID 0 accounts](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image23.png)

Confirmed only root has superuser privileges:

![UID 0 verification](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image28.png)

---

## Task 5: User and Group Policy

### 5.1 Creating Secure Group and Adding Users

Created a new secure group and added the chamberlain user:

![Creating secure group](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image24.png)

### 5.2 Restrict Command Access Using Groups

Created a secure directory with restricted access:

![Creating secure directory](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image25.png)

Verified that users not in the securegroup cannot access the directory:

![Testing restricted access](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image26.png)

The `games` user (not in securegroup) received "Permission denied" when trying to list the `/secure-data` directory contents.

---

## Task 6: Further Steps on Accounts Security

### 6.1 User Account Creation and Management

A new user was created with the enforced password policies:

![Creating new user](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image1.png)

The user was added to the sudo group for administrative privileges:

![Adding user to sudo group](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image2.png)

Successfully switched to the new user account:

![Switching to new user](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image3.png)

### 6.2 Verifying Root User Configuration

Checked the root user entry in `/etc/passwd`:

![Root user details](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image27.png)

The output confirms:
- Username: `root`
- Password field: `x` (password stored in `/etc/shadow`)
- UID: `0` (superuser)
- GID: `0` (root group)
- Home directory: `/root`
- Shell: `/bin/bash`

---

## Task 7: Ensure Login and Logout Events are Collected

### 7.1 Monitoring Login/Logout Events

Displayed the last 10 login sessions:

![Recent login sessions](https://github.com/D-rank-developer/Computer-and-Operating-Systems-Security/blob/8987f91ac4af1d44c70063ad87a2bc6fac9c5848/OS%20Hardening/Lab/password_configuration/image29.png)

Key observations from the output:
- `chamberlain` is currently logged in on `tty3`
- Multiple previous sessions and system reboots are recorded
- The system tracks login duration and session details
- The `/var/log/wtmp` file maintains this audit trail

---

## Summary of Completed Lab Tasks

### ✅ **Completed Security Hardening Measures:**

1. **Password Policies** ✓
2. **System Security Configurations** ✓
3. **User and Group Management** ✓
4. **Monitoring and Auditing** ✓

---

## Conclusion

This comprehensive Linux hardening lab successfully implemented multiple layers of security controls that significantly improve the system's security posture. By following systematic hardening techniques across password policies, system configurations, user management, and monitoring, the environment is better protected against common attack vectors.
