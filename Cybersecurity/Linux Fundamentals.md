[[Linux Common directories]]
### Firsts commands

| Command | Description                                      |
| ------- | ------------------------------------------------ |
| echo    | Output any text that we provide                  |
| whoami  | Find out what user we're currently logged in as! |

### Interacting with the Filesystem

| Command | Full Name               | Purpose                      |
| ------- | ----------------------- | ---------------------------- |
| ls      | listing                 |                              |
| cd      | change directory        |                              |
| cat     | concatenate             |                              |
| pwd     | print working directory |                              |
| touch   | touch                   | Create file                  |
| mkdir   | make directory          | Create a folder              |
| cp      | copy                    | Copy a file or folder        |
| mv      | move                    | Move a file or folder        |
| rm      | remove                  | Remove a file or folder      |
| file    | file                    | Determine the type of a file |
### Searching for files

| Command | Full Name | flag / example                  |
| ------- | --------- | ------------------------------- |
| find    | find      | -name                           |
| grep    | grep      | grep "81.143.211.90" access.log |

### Operators

| Command | Description                    |
| ------- | ------------------------------ |
| &       | run a cmd in the background    |
| >       | output redirector (overwritte) |
| >>      | output redirector (append)     |
### SSH
Secure Shell or SSH simply is a protocol between devices in an encrypted form. Using cryptography, any input we send in a human-readable format is encrypted for travelling over a network -- where it is then unencrypted once it reaches the remote machine, such as in the diagram below.
- SSH allows us to remotely execute commands on another device remotely.
- Any data sent between the devices is encrypted when it is sent over a network such as the Internet

ssh user@MACHINE_IP

![[SSH.png]]

### Permissions 101

| Command | Description                                                    |
| ------- | -------------------------------------------------------------- |
| ls -l   | see files/folders read, write, execute rights by group or user |
| su      | switching between users                                        |

### Utilities

**Downloading files: wget** 
This command allows us to download files from the web via HTTP -- as if you were accessing the file in your browser.
`wget https://assets.tryhackme.com/additional/linux-fundamentals/part3/myfile.txt` 

**Transferring files from your Host: SCP (SSH)**

Secure copy, or SCP, ameans of securely copying files. Unlike the regular cp command, this command allows you to transfer files between two computers using the SSH protocol to provide both authentication and encryption.

Working on a model of SOURCE and DESTINATION, SCP allows you to:

- Copy files & directories from your current system to a remote system
- Copy files & directories from a remote system to your current system

From our machine to a remote one
`scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt`
Reverse
`scp ubuntu@192.168.1.30:/home/ubuntu/documents.txt notes.txt`

**Serving files from your host (Web)**
python3 -m  http.server


### Processes

| Command   | Description                                      | flags                                                                                                                                                                                        |
| --------- | ------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ps        | view processes                                   | aux (all processes)                                                                                                                                                                          |
| top       | real-time statistics about the processes running |                                                                                                                                                                                              |
| kill PID  | terminates process                               | - SIGTERM - Kill the process, but allow it to do some cleanup tasks beforehand<br>- SIGKILL - Kill the process - doesn't do any cleanup after the fact<br>- SIGSTOP - Stop/suspend a process |
| systemctl | Get processes/services to start on Boot          | - Start<br>- Stop<br>- Enable<br>- Disable                                                                                                                                                   |

Note : The process with an ID of 0 is a process that is started when the system boots. This process is the system's init on Ubuntu, such as **systemd**, which is used to provide a way of managing a user's processes and sits in between the operating system and the user.

### Maintaining our system: Automation

We're going to be talking about the `cron` process, but more specifically, how we can interact with it via the use of `crontabs` . Crontab is one of the processes that is started during boot, which is responsible for facilitating and managing cron jobs.

| Value | Description                               |
| ----- | ----------------------------------------- |
| MIN   | What minute to execute at                 |
| HOUR  | What hour to execute at                   |
| DOM   | What day of the month to execute at       |
| MON   | What month of the year to execute at      |
| DOW   | What day of the week to execute at        |
| CMD   | The actual command that will be executed. |
ex: `0 */12 * * * cp -R /home/cmnatic/Documents /var/backups/`

`crontab -e`