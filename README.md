

#                                                #
#      MANAGING FILE PERMISSIONS IN LINUX        #
#                                                #


Project Description
This activity involved managing file permissions in a Linux environment to ensure that the research team's files and directories comply with organizational security policies. The `projects` directory, containing both regular and hidden files, was reviewed and updated. Permissions were analyzed, and unauthorized access was removed where necessary.

The tasks performed included:
1. Checking file and directory details to identify current permissions.
2. Interpreting the 10-character permissions string to understand user, group, and other access levels.
3. Modifying file permissions to remove inappropriate write or execute access.
4. Updating permissions for hidden files to ensure security while retaining functionality.
5. Restricting access to specific directories to authorized users only.

These actions demonstrated the practical use of Linux commands to enforce access controls, which are crucial for protecting sensitive information and maintaining system integrity.

---

### Check File and Directory Details
To analyze the current permissions, I used the `ls -la` command. This command lists all files in the directory, including hidden files, and provides a detailed view of their permissions, ownership, and size.

**Command Used:**
```bash
ls -la
```

**Screenshot Reference:**
<p align="center"> <img src="https://imgur.com/r7PtypR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> <br /> <br />

**Output Analysis:**
- The `projects` directory contained the following:
  - One subdirectory: `drafts`
  - One hidden file: `.project_x.txt`
  - Five project files: `project_k.txt`, `project_t.txt`, `project_m.txt`, etc.
- The permissions were displayed as 10-character strings, which indicate the file type and access levels for the user, group, and others.

---

### Describe the Permissions String
The permissions string is crucial for understanding access levels. It is displayed as a 10-character string in the `ls -la` output and consists of the following parts:
1. **File Type**: The first character is either:
   - `d` for directory.
   - `-` for regular files.
2. **User (Owner) Permissions**: The 2nd-4th characters indicate read (`r`), write (`w`), and execute (`x`) permissions for the file owner.
3. **Group Permissions**: The 5th-7th characters indicate read (`r`), write (`w`), and execute (`x`) permissions for the group associated with the file.
4. **Others (Public) Permissions**: The 8th-10th characters indicate read (`r`), write (`w`), and execute (`x`) permissions for others.

**Example:**
For `project_t.txt`, the permissions string is `-rw-rw-r--`:
- The first character `-` indicates that it is a regular file.
- `rw-`: The user (owner) has read and write permissions but not execute.
- `rw-`: The group has read and write permissions but not execute.
- `r--`: Others have read-only access.

---

### Change File Permissions
The organization prohibits "others" from having write access to files. Upon review, `project_k.txt` was found to have write permissions for others, which violated security policies.

**Command Used:**
```bash
chmod o-w project_k.txt
```

**Screenshot Reference:**
<p align="center"> <img src="https://imgur.com/72dhCxm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> <br /> <br />
**Verification:**
The `ls -la` command was used to confirm that the "write" permission for others was successfully removed. The updated permissions for `project_k.txt` are now `-rw-rw-r--`, meaning others only have read access.

**Detailed Explanation:**
- The `chmod` command modifies file and directory permissions.
- `o-w` removes write permissions from the "others" category.

---

### Change File Permissions on a Hidden File
The `.project_x.txt` file is a hidden file (indicated by the `.` prefix) and was archived. It was determined that no one should have write access to this file, but the user and group should retain read permissions.

**Command Used:**
```bash
chmod u-w,g-w,g+r .project_x.txt
```

**Screenshot Reference:**
<p align="center"> <img src="https://imgur.com/owhrHOC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> <br /> <br />

**Verification:**
The `ls -la` command showed the updated permissions as `-r--r-----`, meaning:
- The user has read permissions but no write or execute permissions.
- The group has read permissions but no write or execute permissions.
- Others have no access.

**Detailed Explanation:**
- `u-w` removes write permissions for the user.
- `g-w` removes write permissions for the group.
- `g+r` adds read permissions for the group.

---

### Change Directory Permissions
The `drafts` directory should only be accessible to the `researcher2` user. It was found that the `research_team` group had execute permissions, allowing them to access the directory. This access was restricted.

**Command Used:**
```bash
chmod g-x drafts
```

**Screenshot Reference:**
<p align="center"> <img src="https://imgur.com/owhrHOC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> <br /> <br />

**Verification:**
The `ls -la` command showed the updated permissions as `drwx-----`, meaning:
- Only the user has read, write, and execute permissions.
- The group and others have no permissions.

**Detailed Explanation:**
- The `chmod g-x` command removes execute permissions for the group, ensuring that only the owner can access the directory.

---

### Summary
This activity involved a comprehensive review and update of file and directory permissions in the `projects` directory. Key actions included:
1. Using the `ls -la` command to analyze permissions for all files, including hidden ones.
2. Understanding the permissions string to identify inappropriate access levels.
3. Modifying permissions with `chmod` to comply with security policies:
   - Removing write permissions for others.
   - Restricting access to hidden files.
   - Limiting directory access to authorized users only.

By completing these tasks, I demonstrated the ability to analyze and enforce access control policies in a Linux environment, which is essential for protecting sensitive data and maintaining system integrity.
