
Activity Title: Managing Authorization in Linux Using Bash Commands

Overview

This activity involved using Linux commands in a Bash shell environment to analyze, manage, and configure file and directory permissions. Managing file permissions is a critical component of system security, as it ensures that unauthorized users cannot access or modify sensitive files and directories. By completing this lab, I gained hands-on experience with Linux commands such as ls, chmod, cd, and others to enforce proper authorization policies.

Scenario

In this scenario, I worked with the /home/researcher2/projects directory, which contains multiple files and subdirectories. The researcher2 user is a member of the research_team group. The primary objective was to audit file and directory permissions and ensure that they adhered to security requirements. Unauthorized access was identified and removed, and permissions were modified to strengthen the overall security of the system.

The lab tasks involved the following goals:
1. Check file and directory permissions to identify any incorrect configurations.
2. Adjust file permissions to ensure that only authorized users have access.
3. Manage the permissions of hidden files to prevent unintended access.
4. Configure directory permissions to restrict access to sensitive folders.

Tasks Completed

Task 1: Check File and Directory Details
1. Navigated to the /home/researcher2/projects directory using the `cd` command.
2. Listed the contents of the directory and their permissions using the `ls -l` command.
   - Observed that the group research_team owned all files and directories.
   - Permissions for files included read, write, and execute privileges for various owner types.
3. Checked for hidden files in the directory using `ls -la`.
   - Identified that the file .project_x.txt was hidden within the directory.

Task 2: Change File Permissions
1. Analyzed the permissions of each file to identify incorrect configurations.
   - Used `ls -l` to identify that project_k.txt had write permissions for "other users," which is a security risk.
   - Modified the permissions of project_k.txt using `chmod o-w project_k.txt` to remove write access for other users.
2. Verified that the file project_m.txt should only be accessible to the user (read and write permissions) and not the group or others.
   - Observed that the group had read permissions, which violated the restriction.
   - Used `chmod g-r project_m.txt` to remove read permissions for the group.
3. Re-verified permissions using `ls -l` to confirm the changes were applied successfully.

Task 3: Change Permissions of a Hidden File
1. Checked the permissions of the hidden file .project_x.txt using `ls -la`.
   - Observed that both the user and the group had write permissions, which was unnecessary for an archived file.
2. Modified the permissions to allow read-only access for both the user and the group while removing write access.
   - Applied `chmod u-w,g-w,g+r .project_x.txt` to enforce the changes.
3. Confirmed the updated permissions using `ls -la`:
   - The file was now readable by the user and group but not writable.

Task 4: Change Directory Permissions
1. Checked the permissions of the drafts directory within the projects directory using `ls -l`.
   - Observed that the group research_team had execute permissions, allowing them to access the directory contents.
2. Removed execute permissions for the group to restrict access, ensuring that only the researcher2 user could access the drafts directory and its contents.
   - Used `chmod g-x drafts` to apply the restriction.
3. Verified the updated permissions using `ls -l` to ensure the changes were correctly applied.

Skills Demonstrated
1. **File Permission Management:**
   - Accurately analyzed file and directory permissions using `ls -l` and `ls -la`.
   - Effectively applied the `chmod` command to modify permissions for specific owner types (user, group, others).

2. **Hidden File Security:**
   - Identified hidden files using `ls -la` and ensured their permissions were correctly configured.
   - Applied restrictions to sensitive files to align with security policies.

3. **Authorization and Access Control:**
   - Restricted access to files and directories by removing unnecessary write and execute permissions.
   - Ensured compliance with the principle of least privilege by limiting access to only authorized users.

4. **Practical Command-Line Experience:**
   - Used essential Linux commands (`cd`, `ls`, `chmod`) to navigate and manage file systems effectively.
   - Gained proficiency in understanding and configuring file permission strings.

Conclusion
This activity reinforced my understanding of Linux file and directory permissions and their critical role in maintaining system security. By completing the tasks, I demonstrated my ability to audit and modify permissions to prevent unauthorized access. These skills are fundamental for protecting sensitive information and ensuring secure system operations.

<p align="center">
<img src="https://imgur.com/r7PtypR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<p align="center">
<img src="https://imgur.com/72dhCxm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<p align="center">
<img src="https://imgur.com/owhrHOC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
