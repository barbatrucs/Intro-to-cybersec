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


### System Configuration panel

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


##### System Information
msinfo32
Per Microsoft, "_Windows includes a tool called Microsoft System Information (Msinfo32.exe).  This tool gathers information about your computer and displays a comprehensive view of your hardware, system components, and software environment, which you can use to diagnose computer issues._"

The  information in **System Summary** is divided into three sections:

- **Hardware Resources**
- **Components**
- **Software Environment**

Per [Microsoft](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_environment_variables?view=powershell-7.1), "_Environment variables store information about the operating system environment. This information includes details such as the operating system path, the number of processors used by the operating system, and the location of temporary folders._

_The environment variables store data that is used by the operating system and other programs. For example, the WINDIR environment variable contains the location of the Windows installation directory. Programs can query the value of this variable to determine where Windows operating system files are located_".

Another method to view environment variables is `Control Panel > System and Security > System > Advanced system settings > Environment Variables` **OR** `Settings > System > About > system info > Advanced system settings > Environment Variables`.


##### Resource Monitor

resmon
Per Microsoft, "_Resource Monitor displays per-process and aggregate CPU, memory, disk, and network usage information, in addition to providing details about which processes are using individual file handles and modules. Advanced filtering allows users to isolate the data related to one or more processes (either applications or services), start, stop, pause, and resume services, and close unresponsive applications from the user interface. It also includes a process analysis feature that can help identify deadlocked processes and file locking conflicts so that the user can attempt to resolve the conflict instead of closing an application and potentially losing data._"

##### Command Prompt

cmd
hostname = Computer Name
whoami = name of the logged-in user
ipconfig = network address settings for the computer
/? = manual for a cmd
cls = clear the command prompt
netstat = display protocol statistics and current TCP/IP network connections.
net user =

Refer to the following link to see a comprehensive list of commands you can execute in the command prompt [here](https://ss64.com/nt/).


##### Registry Editor

_regedt32.exe_
The **Windows Registry** (per Microsoft) is a central hierarchical database used to store information necessary to configure the system for one or more users, applications, and hardware devices.

The registry contains information that Windows continually references during operation, such as:

- Profiles for each user
- Applications installed on the computer and the types of documents that each can create
- Property sheet settings for folders and application icons
- What hardware exists on the system
- The ports that are being used.

### Windows security features

##### Windows Update

Windows Update is a service provided by Microsoft to provide security updates, feature enhancements, and patches for the Windows operating system and other Microsoft products, such as Microsoft Defender. 

Updates are typically released on the 2nd Tuesday of each month. This day is called **Patch Tuesday**. That doesn't necessarily mean that a critical update/patch has to wait for the next Patch Tuesday to be released. If the update is urgent, then Microsoft will push the update via the Windows Update service to the Windows devices.

Windows Update is located in Settings.

**Tip**: Another way to access Windows Update is from the Run dialog box, or CMD, by running the command `control /name Microsoft.WindowsUpdate`.

Throughout the years, Windows users have grown accustomed to pushing Windows Updates off to a later date or not installing the updates at all. Various reasons caused this action, one being the fact that a reboot is typically required after a Windows update.  

Microsoft notably addressed this issue with Windows 10. The updates can no longer be ignored or pushed to the side until forgotten. Windows updates can only be postponed, but eventually, the update will happen, and your computer will reboot. Microsoft provides these updates to keep the device safe and secure.

##### Windows Security

Per Microsoft, "_**Windows Security** is your home to manage the tools that protect your device and your data_".

In case you missed it, **Windows Security** is also available in **Settings**.

**Protection areas**.
- **Virus & threat protection**
- **Firewall & network protection**
- **App & browser control**
- **Device security**

quick comment on the status icons.
- **Green** means your device is sufficiently protected, and there aren't any recommended actions.
- **Yellow** means there is a safety recommendation for you to review.
- **Red** is a warning that something needs your immediate attention.

###### Virus & threat protection

divided into two parts:  
- **Current threats**
- **Virus & threat protection settings**

###### Firewall & network protection

What is a **firewall**?
Per Microsoft, "_Traffic flows into and out of devices via what we call ports. A firewall is what controls what is - and more importantly isn't - allowed to pass through those ports. You can think of it like a security guard standing at the door, checking the ID of everything that tries to enter or exit_".

Per Microsoft, "_Windows Firewall offers three firewall profiles: domain, private and public"._
- **Domain** - _The domain profile applies to networks where the host system can authenticate to a domain controller._ 
- **Private** - _The private profile is a user-assigned profile and is used to designate private or home networks._
- **Public** - _The default profile is the public profile, used to designate public networks such as Wi-Fi hotspots at coffee shops, airports, and other locations._

**Tip:** Command to open the Windows Defender Firewall is `WF.msc`.

######  App & browser Control

Per Microsoft, "_Microsoft Defender SmartScreen protects against phishing or malware websites and applications, and the downloading of potentially malicious files_".

**Check apps and files**
- **Windows Defender SmartScreen** helps protect your device by checking for unrecognized apps and files from the web.

**Exploit protection**
- Exploit protection is built into Windows 10 (and, in our case, Windows Server 2019) to help protect your device against attacks.

###### Device security

**Core isolation**
- **Memory Integrity** - Prevents attacks from inserting malicious code into high-security processes.

What is the **Trusted Platform Module** (**TPM**)?  
Per Microsoft, "_Trusted Platform Module (TPM) technology is designed to provide hardware-based, security-related functions. A TPM chip is a secure crypto-processor that is designed to carry out cryptographic operations. The chip includes multiple physical security mechanisms to make it tamper-resistant, and malicious software is unable to tamper with the security functions of the TPM_".


##### Bitlocker

What is **BitLocker**?
Per Microsoft, "_BitLocker Drive Encryption is a data protection feature that integrates with the operating system and addresses the threats of data theft or exposure from lost, stolen, or inappropriately decommissioned computers_".

On devices with TPM installed, BitLocker offers the best protection.

##### Volume Shadow Copy service

Per [Microsoft](https://docs.microsoft.com/en-us/windows-server/storage/file-server/volume-shadow-copy-service), the Volume Shadow Copy Service (VSS) coordinates the required actions to create a consistent shadow copy (also known as a snapshot or a point-in-time copy) of the data that is to be backed up. 

Volume Shadow Copies are stored on the System Volume Information folder on each drive that has protection enabled.  

If VSS is enabled (**System Protection** turned on), you can perform the following tasks from within **advanced system settings**:
- **Create a restore point**
- **Perform system restore**
- **Configure restore settings**
- **Delete restore points**

From a security perspective, malware writers know of this Windows feature and write code in their malware to look for these files and delete them. Doing so makes it impossible to recover from a ransomware attack unless you have an offline/off-site backup.