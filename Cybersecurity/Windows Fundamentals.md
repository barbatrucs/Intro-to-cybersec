### The File System

Current :
New Technology File System (NTFS)

Old :
- FAT16/FAT32 (File Allocation Table)
- HPFS (High Performance File System)

FAT partition is still use in USB, MicroSD, etc but not traditionally in Windows computers or Windows servers.


NTFS is known as a j**ournaling file system**. In case of a failure, the file system **can automatically repair the folders/files on disk using information stored in a log file**. This function is not possible with FAT.

NTFS addresses many of the limitations of the previous file systems; such as: 
- Supports files larger than 4GB
- Set specific permissions on folders and files
- Folder and file compression
- Encryption ([Encryption File System](https://docs.microsoft.com/en-us/windows/win32/fileio/file-encryption) or **EFS**)

On NTFS volumes, you can set permissions that grant or deny access to files and folders.

The permissions are:
- **Full control**
- **Modify**
- **Read & Execute**
- **List folder contents**
- **Read**
- **Write**

##### **Alternate Data Streams** (**ADS**)

Alternate Data Streams (ADS) is a file attribute specific to Windows NTFS (New Technology File System).

Every file has at least one data stream (`$DATA`), and ADS allows files to contain more than one stream of data. Natively [Window Explorer](https://support.microsoft.com/en-us/windows/what-s-changed-in-file-explorer-ef370130-1cca-9dc5-e0df-2f7416fe1cb1) doesn't display ADS to the user. There are 3rd party executables that can be used to view this data, but [Powershell](https://docs.microsoft.com/en-us/powershell/scripting/overview?view=powershell-7.1) gives you the ability to view ADS for files.

From a security perspective, malware writers have used ADS to hide data.

Not all its uses are malicious. For example, when you download a file from the Internet, there are identifiers written to ADS to identify that the file was downloaded from the Internet.

### The Windows\System32 Folders

**C: \\ Windows :** Traditionally the folder containing Windows operating system. The folder doesn't have to reside in the C drive necessarily. It can reside in any other drive and technically can reside in a different folder.
This is where environment variables, more specifically system environment variables, come into play. Even though not discussed yet, the system  environment variable for the Windows directory is `%windir%`.

Per [Microsoft](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_environment_variables?view=powershell-7.1), "_Environment variables store information about the operating system environment. This information includes details such as the operating system path, the number of processors used by the operating system, and the location of temporary folders_".

The **System32** folder holds the important files that are critical for the operating system.

You should proceed with extreme caution when interacting with this folder. Accidentally deleting any files or folders within System32 can render the Windows OS inoperational. Read more about this action [here](https://www.howtogeek.com/346997/what-is-the-system32-directory-and-why-you-shouldnt-delete-it/). 

**Note**: Many of the tools that will be covered in the Windows Fundamentals series reside within the System32 folder.

### User Accounts, Profiles, and Permissions

User accounts can be one of two types on a typical local Windows system: **Administrator** & **Standard User**. 

The user account type will determine what actions the user can perform on that specific Windows system.

- An Administrator can make changes to the system: add users, delete users, modify groups, modify settings on the system, etc. 
- A Standard User can only make changes to folders/files attributed to the user & can't perform system-level changes, such as install programs.

When a user account is created, a profile is created for the user. The location for each user profile folder will fall under is C:\Users.

The creation of the user's profile is done upon initial login. When a new user account logs in to a local system for the first time, they'll see several messages on the login screen. One of the messages, User Profile Service, sits on the login screen for a while, which is at work creating the user profile. See below.

A way to access this information, and then some, is using **Local User and Group Management**. Right-click on the Start Menu and click **Run**. Type `lusrmgr.msc`.

### User Account Control

**Note**: UAC (by default) doesn't apply for the built-in local administrator account. 

How does UAC work? When a user with an account type of administrator logs into a system, the current session doesn't run with elevated permissions. When an operation requiring higher-level privileges needs to execute, the user will be prompted to confirm if they permit the operation to run.``


### System Configuration

##### MSConfig
the SytemConfiguration utility is for advanced troubleshooting and its main purpose is to help diagnose startup issues.

Reference the following document [here](https://docs.microsoft.com/en-us/troubleshoot/windows-client/performance/system-configuration-utility-troubleshoot-configuration-errors) for more information on the System Configuration utility.

The utility has five tabs across the top. Below are the names for each tab. We will briefly cover each tab in this task. 

1. General
In the **General** tab, we can select what devices and services for Windows to load upon boot. The options are: **Normal**, **Diagnostic**, or **Selective**.

2. Boot
In the **Boot** tab, we can define various boot options for the Operating System.

3. Services
The **Services** tab lists all services configured for the system regardless of their state (running or stopped). A service is a special type of application that runs in the background.

4. Startup
Microsoft advises using **Task Manager (**`taskmgr`**)** to manage (enable/disable) startup items. The System Configuration utility is **NOT** a startup management program.

5. Tools
There is a list of various utilities (tools) in the Tools tab that we can run to configure the operating system further. There is a brief description of each tool to provide some insight into what the tool is for.

##### Compmgmt
The **Computer Management** utility has three primary sections: System Tools, Storage, and Services and Applications.

