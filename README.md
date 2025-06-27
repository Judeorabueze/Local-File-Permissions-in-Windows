# Managing Local File Permissions in Windows Environment

## Introduction
This project demonstrates my hands-on experience in managing file and folder permissions in a Windows environment. It details the process of managing user accounts and local file/folder permissions on a Windows 11 virtual.

This task was completed in response to a training ticket assigned during my hands-on Practical Help Desk course with LevelEffect. The goal was to remove administrators priviledge of a user by making the user's account a regular one and to also deny the user access to a file (salary.txt) saved in the Windows 11 local Disk (C:).

## Lessons Learnt
Through this project, I learned how easily inherited permissions can expose sensitive files if not properly managed. I also deepened my understanding of how Deny permissions take precedence. This exercise reinforced my understanding of the principle of least privilege and its real-world application.

## Ticket
![Ticket](https://github.com/Judeorabueze/Local-File-Permissions-in-Windows/blob/main/ticket.PNG)

## Objectives
- To demonstrate the ability to manage file and folder permissions in Windows
- To restrict access to sensitive files based on user roles
- To apply the principles of least privilege and access control
- To show proficiency in using built-in Windows tools for security management
- To document a repeatable approach for applying permissions in real-world scenarios

## Tools and Technologies
- Windows 11 (Virtual Machine)
- Local Users and Groups (`lusrmgr.msc`)
- NTFS File System
- File Explorer Security Tab

## Aproach Adopted

### 1. Change local user account (Richard) fron admin group to a standard / regular user.

<b>Method 1: Using Local Users and Groups (GUI)</b>
-  Open Local Users and Groups
    - Press `Win + R` type `lusrmgr.msc`, and press `Enter`.
- In the left pane, click on "Users".
- In the middle pane, find and double-click on "Richard".
- In the "Richard Properties" window, go to the "Member Of" tab.

![Local User](https://github.com/Judeorabueze/Local-File-Permissions-in-Windows/blob/main/Loca%20User.PNG)

- Select "Administrators" and click Remove.
- Since "Users" is already in Richards "Member Of" page, click 'Apply' and then 'OK'.
- 
![local user 2](https://github.com/Judeorabueze/Local-File-Permissions-in-Windows/blob/main/Local%20user%202.PNG)

The user "Richard" has successfully been removed from Administrators group and made a regular User.

<b> Method 2: Using Command Prompt (Admin)</b>
- Search for cmd or Command Prompt on Windows.
- Click on 'Run as administrator'
- In the CLI, enter `net localgroup Administrators` to check the list of local administrators on a Windows system 

![Admin List](https://github.com/Judeorabueze/Local-File-Permissions-in-Windows/blob/main/Admin.PNG)

From the screenshot above, the user "Richard" was in Administrators group.

- Remove "Richard" from Administrators group, enter `net localgroup Administrators Richard /delete`
- Add User "Richard" to standard User group, enter `net localgroup Users Richard /add`
- Check users in Administrators group, enter `net localgroup Administrators`
- Check users in Users group, enter `net localgroup Users`

![user check](https://github.com/Judeorabueze/Local-File-Permissions-in-Windows/blob/main/User%20group%20cli.PNG)

Alternatively, enter `net user Richard` to confirm the local user "Richard"



From the screenshot above, user "Richard" has been removed from Administrators group and now a standard user.

### 2. Change local user account (Richard) fron admin group to a standard / regular user.
