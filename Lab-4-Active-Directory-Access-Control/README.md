# Lab 4 - Active Directory Group Based Access Control and Network Share Permissions

## Overview
This lab demonstrates how to configure Active Directory users, security groups, and shared folder permissions in a Windows domain environment. The objective was to simulate a real world IT scenario where access to shared resources is controlled using group based permissions and NTFS security.

---

## Lab Setup
- Host Machine: Windows Laptop  
- Virtualization: VMware Workstation Player  
- Domain Controller: Windows Server 2022 DC1  
- Client Machine: Windows 10 or Windows 11 VM domain joined  
- Domain: corp.local  
- Network Type: NAT same subnet  

---

## Tools Used
- Active Directory Users and Computers  
- Server Manager  
- File Explorer Network Shares  
- Command Prompt  
- gpupdate  
- whoami  

---

## Network Configuration
- Domain Controller assigned private IP address  
- Client VM assigned private IP address on same subnet  
- Verified connectivity using ping  
- Client successfully joined domain  

---

## Tasks Performed

### 1. Active Directory User Creation
- Opened Active Directory Users and Computers  
- Navigated to corp.local Users  
- Created user John Test (jtest)  
- Created user HR User (hr_user)  
- Set passwords and enabled accounts  

![User Creation](screenshots/user-creation.png)

---

### 2. Security Group Creation
- Created SharedFolderUsers group  
- Created HR_Users group  
- Set both as Global Security groups  
- Added jtest to SharedFolderUsers  
- Added hr_user to HR_Users  

![Group Membership](screenshots/group-membership.png)

---

### 3. Shared Folder Creation
- Created C:\SharedFolder  
- Created C:\HR_Folder  
- Enabled sharing  
- SharedFolder accessible at \\DC1\SharedFolder  
- HR_Folder accessible at \\DC1\HR_Folder  

---

### 4. Share Permissions Configuration
- Configured sharing permissions for SharedFolder  
- Removed unnecessary default access  
- Added SharedFolderUsers with permissions  
- Configured sharing permissions for HR_Folder  
- Added HR_Users with permissions  

![Share Permissions](screenshots/shared-folder.png)

---

### 5. NTFS Permissions Configuration
- Opened folder properties Security Advanced  
- Disabled inheritance  
- Converted inherited permissions  
- Removed default Users group  
- Added SharedFolderUsers permissions  
- Added HR_Users permissions  
- Kept Administrators and SYSTEM full control  

![NTFS Permissions](screenshots/ntfs-permissions.png)

---

### 6. Client Machine Testing

#### Access Denied Test
- Logged in as jtest  
- Accessed SharedFolder successfully  
- Attempted HR_Folder and received access denied  

![Access Denied](screenshots/access-denied.png)

---

#### Successful Access Test
- Logged in as hr_user  
- Accessed HR_Folder successfully  
- Attempted SharedFolder and received access denied  

![Access Success](screenshots/access-success.png)

---

### 7. Group Membership Verification
- Opened Command Prompt  
- Ran whoami /groups  
- Verified group membership for each user  

![Whoami Groups](screenshots/whoami-groups.png)

---

### 8. Group Policy Update
- Ran gpupdate /force  
- Logged out and logged back in  
- Confirmed permissions applied  

---

### 9. Permission Troubleshooting
- Removed jtest from SharedFolderUsers  
- Verified access was denied  
- Re added jtest  
- Logged out and logged back in  
- Verified access restored  

---

### 10. Inheritance and Security Control
- Observed inherited permissions  
- Disabled inheritance  
- Removed unnecessary default groups  
- Applied least privilege model  

---

## Results
- Created Active Directory users and groups  
- Implemented group based access control  
- Verified proper access and restrictions  
- Demonstrated department level separation  
- Successfully tested permission changes  

---

## Key Takeaways
- Active Directory user and group management  
- NTFS vs share permissions  
- Permission inheritance control  
- Role based access control  
- File sharing in a domain environment  
- Group membership directly impacts access  
- Troubleshooting permission issues  

---

## Conclusion
This lab simulates a real world enterprise IT environment where users require controlled access to shared resources. By using security groups instead of assigning permissions directly to users, access control becomes scalable and secure. This lab also reinforced troubleshooting techniques and validation methods which are critical in IT support and system administration roles.
