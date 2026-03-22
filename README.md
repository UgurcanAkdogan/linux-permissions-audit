# linux-permissions-audit
Audit and management of Linux file permissions to implement the principle of least privilege as part of the Google Cybersecurity Professional Certificate.
Linux File Permissions Audit
Project Description

In this project, I performed a security audit on a Linux system to manage file and directory permissions. The primary goal was to implement the Principle of Least Privilege (PoLP), ensuring that users and groups have only the access necessary for their specific roles, thereby reducing the system's attack surface.
Lab Environment

    Platform: Google Cybersecurity Professional Certificate (Coursera)

    Operating System: Linux (Bash Shell)

    Key Tools: chmod, ls -la, cd

🛠️ Step-by-Step Security Audit
1. Initial Inspection of Permissions

I navigated to the projects directory and listed all files, including hidden ones, to audit the current permission strings.
Bash

cd projects
ls -la

    Action: Investigated the 10-character permission strings to identify unauthorized access.

2. Modifying File Permissions

I identified that project_x.txt allowed "others" to have write access. I removed this permission to prevent unauthorized modifications.

    Command: chmod o-w project_x.txt

    Result: Successfully removed write access for the "other" group.

3. Securing Hidden Files

Hidden files often contain sensitive data. I audited .project_x.txt and removed write permissions for both the user and the group to make it "read-only."

    Command: chmod ug-w .project_x.txt

    Result: Hardened the hidden file against accidental or malicious changes.

4. Restricting Directory Access

I modified the permissions of the drafts directory to prevent group members from entering or executing files within it.

    Command: chmod g-x drafts

    Result: Removed the "execute" (x) bit, effectively blocking group access to the directory contents.

🎯 Key Takeaways

    System Hardening: Reducing file permissions is a critical step in securing a Linux environment.

    Granular Control: Practiced using chmod with symbolic links (u, g, o) to manage specific access levels.

    Audit Methodology: Learned how to use ls -la to identify hidden security risks in the file system.

👤 About the Author

I am Uğurcan, an aspiring Cybersecurity Professional and SOC Analyst. I am currently focusing on Linux security, system hardening, and threat detection.
