# Linux Introduction
## Why Linux?
- OpenSource
- Community support
- Heavily customizable
- Most Servers runs on Linux
- DevOps most of the tools implements on Linux only
- Automation
- Secure

## Architecture of Linux

| Layer | Software |
|--|--|
| Innermost | Kernel (Linux) |
| Middle | Shell |
| Uppermost | User Applications |

> **note**: Kernel is the software that connects hardware with software. Think it as a bridge between them.

## Diffrent Linux distros
### Popular Desktop Linux OS
- Ubuntu
- Linux Mint
- Arch Linux
- Fedora
- Debian
- OpenSuse

### Popular Server Linux OS
- Red Hat Enterprise Linux
- Ubuntu Server
- Debian minimal
- Centos
- SUSE Enterprise Linux

### Most used Linux distros currently in IT
- **industry. RPM based**: RHEL & Centos
- **Debian based**: Ubuntu Server & Debian

## Some important directories

| Type | Directory |
|-------------------------|-----------------------------------|
| Home | /root, /home/username |
| User Executable | /bin, /usr/bin, /usr/local/bin |
| System Executables | /sbin, /usr/sbin, /usr/local/sbin |
| Other Mountpoints  | /media, /mnt |
| Configuration | /etc |
| Temporary Files | /tmp |
| Kernels and Bootloaders | /boot |
| Server Data | /var, /srv |
| System Information | /proc, /sys |
| Shared Libraries | /lib, /usr/lib, /usr/local/lib |

## File types in Linux

| File Type | char | Description |
|--|--|--|
| Regular file | - | Normal files such as text, data, executable file |
| Directory | d | Files that are lists of other files |
| Link | l | shortcut that points to the location of actual file |
| Special file | c | mechanism for input and output, like files in /dev |
| Socket | s | special file that gives inter-process networking |
| Pipe | p | special file that allows processes to communicate |

> **note**: Symbolic links Symbolic links are like desktop shortcuts we use in windows. Create a soft link for /var/log directory in our current working directory.

## Difference between RPM based and Debian based

From user's point of view, there isn't much difference in these tools. The RPM and DEB formats are both just archive files, with some metadata attached to them. They are both equally arcane, have hardcoded install paths and only differ in subtle details. DEB files are installation files for Debian based distributions. RPM files are installation files for Red Hat based distributions. Ubuntu is based on Debian's package manage based on APT and DPKG. Red Hat, CentOS and Fedora are based on the old Red Hat Linux package management system, RPM.

### DEB or .deb (Debian based softwares)
DEB is the extension of the Debian software package format and the most often used name for such binary packages. DEB was developed by Debian.

**Example**: Google chrome software  
**Package name**: google-chrome-stable_current_amd64.deb  
**Installation**:
``` bash
dpkg -i google-chrome-stable_current_amd64.deb
```

### RPM or .rpm (Red Hat based softwares.)
It is a package management system. The name RPM variously refers to the #.rpm# file format, files in this format, software packaged in such files, and the package manager itself. RPM was intended primarily for Linux distributions; the file format is the baseline package format of the Linux Standard Base. RPM was developed by Community & Red Hat.

**Example**: Google chrome software  
**Package name**: google-chrome-stable-57.0.2987.133-1.x86_64.rpm  
**Installation**:
``` bash
rpm -ivh google-chrome-stable-57.0.2987.133-1.x86_64.rpm
```
_note_: You will also encounter diffrent commands, packages and service names while using both kinds of distros.

## Basic Commands
- Open Terminal (Tmux in Terminator is always preferred!)
- Know where you are? Present Working Directory
  ``` bash
  pwd
  ```

- List all the files in a directory
  ``` bash
   $ ls # list everything in the current directory
   $ ls Documents # list everything in the Documents directory
  ```
| Options | Description                                                |
|---------|------------------------------------------------------------|
| -l      | Long listing format of files and directories, one per line |
| -a      | List all hidden files and directories started with '.'     |
| -F      | Add a '/' classification at the end of each directory      |
| -g      | List all files and directories with the group name         |
| -i      | Print index number of each files and directories           |
| -m      | List all file and directories separated by comma ','       |
| -n      | List numeric UID and GID of Owner and Groups               |
| -r      | List all files and directories in reverse order            |
| -R      | Short liat all directories                                 |
| -t      | Sorted by modified time, started with the newest file      |

- Create a directory/folder in your home directory.
  ``` bash
  mkdir my_fav_folder
  ```

- Change your current working directory to linux-practices(Go to _Documents_ folder).
  ``` bash
  cd Documents
  ```

- Create some more directories and list them with "ls" command.
  ``` bash
  $ mkdir vpdir
  $ mkdir testdir
  $ mkdir devopsdir
  $ ls
  ```

- Create some empty files with "touch" command and list them.
  ``` bash
  $ touch file1 file2 file3
  $ ls
  ```

## Absolute path and Relative path
### What is a path?
A path is a unique location to a file or a folder in a file system of an OS. A path to a file is a combination of / and alpha-numeric characters.

### What is an absolute path?
An absolute path is defined as the specifying the location of a file or directory from the root directory(/). In other words we can say absolute path is a complete path from start of actual filesystem from / directory.

**Some examples of absolute path**:
- /home/rootkit/linux-practices
- /var/ftp/pub
- /etc/samba.smb.conf
- /boot/grub/grub.conf

If you see all these paths started from / directory which is a root directory for every Linux/Unix machines.

### What is the relative path?
Relative path is defined as path related to the present working directory(pwd). Suppose I am located in _/home/rootkit_ and I want to change directory to _/home/rootkit/codes_. I can use relative path concept to change directory to _codes_ and also devopsdir directory.

_note_: All these paths do not start with / directory.

### some commands
#### Creating directories in devopsdir directory with absolute and relative path
``` bash
mkdir devops/ansible
mkdir /home/rootkit/linux/devops/aws
ls devops/
```

#### Copying files into directory
``` bash
$ cp file1 testdir
$ cd testdir
$ ls
```

#### Copying directories from one location to another
``` bash
cp -rvfp testdir vpdir
```

#### Moving files from one location to another
``` bash
mv file2 vpdir/
```

#### Removing files and directories
``` bash
$ rm file1 # removes a file
$ rm -rf testdir # removes a folder
```

#### Read files
``` bash
cat file2.py
```

## Neovim Editor
### quick start

- Install neovim editor
  > _Note_: Installation is for **Debian, Arch Linux and their derivatives**.
  ``` bash
  $ sudo apt install neovim # for Debian and its derivatives
  $ sudo pacman -S neovim # for Arch Linux and its derivatives
  ```

- Open up a file in neovim editor
  ``` bash
  nvim sample.py
  ```

- Hit i to enter into insert mode
- type few lines
- hit Esc
- type `:wq`
- Enter

## a brief introduction

VI Visual display editor VIM Visual display editor improved. Neovim is more customizable then VIM inheriting all the vim commands and default key bindings.

This is command mode editor for files. Other editors in Linux are emacs, gedit, nano vi editor is most popular.

It has 3 modes:
  1. Command Mode
  2. nsert mode (edit mode)
  3. extended command mode

_note_: When you open the neovim editor, it will be in the command mode by default.

### Normal Mode:

| keybinding | function                                                |
|------------|---------------------------------------------------------|
| gg         | go to the beginning of the page                         |
| G          | go to the end of the page                               |
| 0          | go to the beginning of the line                         |
| $          | go to the end of the line                               |
| w          | move the cursor forward, word by word                   |
| b          | move the cursor backward, word by word                  |
| nw         | move the cursor forward to n words                      |
| nb         | move the cursor backward to n words                     |
| u          | undo last change (word)                                 |
| U          | undo the previous changes (entire line)                 |
| Ctrl + R   | redo the changes                                        |
| A          | go to last of the current line with insert mode enabled |
| yy         | copy a line                                             |
| nyy        | copy n lines                                            |
| p          | paste line below the cursor position                    |
| P          | paste line above the cursor position                    |
| dw         | delete the word letter by letter (like Backspace)       |
| x          | delete the word letter by letter (like DEL key)         |
| dd         | delete entire line                                      |
| ndd        | delete n no. of lines from cursor position              |
| /          | search a word in the file                               |

### Command Mode: ( Colon Mode)

| command  | function                                      |
|----------|-----------------------------------------------|
| :w       | save changes                                  |
| :q       | quit (without saving)                         |
| :wq      | save and quit                                 |
| :w!      | save forcefully                               |
| :wq!     | save and quit forcefully                      |
| :x       | save and quit                                 |
| :X       | give password to the file and remove password |
| :20(n)   | go to line no 20 or n                         |
| :se nu   | set the line numbers to the file              |
| :se nonu | remove the set line numbers                   |

# Filter & IO redirection command
## Grep

**grep** command is used to search for patterns within files.

> _Passwd_ file: stores information about all the users in the system
``` bash
cat /etc/passwd
```

- Finding line which contains word as "root" from _/etc/passwd_ file.
  ``` bash
  grep "root" /etc/passwd
  ```

- Search for pattern using **basic** regular expressions (grep's default behavior):
  > **NOTE**: Supports (^, $, ., [abc], [^abc], [a-z], *, \)  
  ``` bash
  grep -G "^alias" ~/.bashrc
  ```

  > **NOTE**: grep uses `-G` by default so this option is redundant.

- Interprets patterns as **extended** regular expressions:
  > **NOTE**: Supports (?, +, {}, (), and |)  
  ``` bash
  grep -E "yt-dlp|lsp" .bashrc
  ```

- Interprets patterns as **fixed strings** rather regular expressions (**disables regex**):  
  ``` bash
  grep -F "fixed string" /etc/passwd
  ```

- Search for a pattern in all files **recursively** in a directory:
  ``` bash
  grep -r "xrandr" .cache
  ```

- **Ignore binary** files, search **recursively** in a directory, and print **file names** rather than the normal line output:
  ``` bash
  grep -Irl "neovim" .config
  ```

- An inverse search for the pattern (returns lines that **DO NOT contain** the pattern):
  ``` bash
  grep -v "^#" .bashrc
  ```

- Search for pattern, **ignoring** case and adding **line numbers** to the output:
  ``` bash
  grep -in "yt" .bashrc
  ```

- Recursively search and do not write anything to standard output (**quiet** mode):
  ``` bash
  grep -rq "wax$" .zshrc
  ```

- Recursively search and **suppress** error messages about non-existent or unreadable files:
  ``` bash
  grep -rs "lol" .zshrc
  ```

- Set a **max** number of matching lines:
  ``` bash
  grep -m 2 "bin" /opt/samp.txt
  ```

## Filter Commands

- **less**: Displays file content page wise or line wise.
  ``` bash
  less /etc/passwd
  ```

| keybinding | Description                     |
|------------|---------------------------------|
| d          | go to the next page             |
| b          | go to the previous page         |
| /          | search for a word in the file   |
| v          | go to vi mode and edit the file |

- **more**: It is exactly same line `less`
  ``` bash
  more /etc/passwd
  ```

| keybinding | Description                     |
|------------|---------------------------------|
| Enter      | scroll down line by line        |
| d          | go to the next page             |
| /          | search for a word in the file   |
| v          | go to vi mode and edit the file |

- **head**: It is used to display the #top 10 lines# of the file.
  ``` bash
  head /etc/passwd
  ```

- **tail**: It is used to display the #last 10 lines# of the file.
  ``` bash
  tail /etc/passwd
  ```

- **cut**:
  ``` bash
  cut -d " " -f <file_name>
  ```

Here,
- `-d` stands for delimeter e.g. :, " " etc
- `-f` stands for field

The above command delimit all spces and print the field.

## sed

The **sed** command is a very powerful shell utility that is used to filter and transform text.

- Replace first instance on each line of **old** with **new** using basic regex and print to stdout:
  ``` bash
  command | sed 's/old/new/'
  ```

- Replace **old** with **new** on all lines using basic regex and print to stdout:
  ``` bash
  sed 's/old/new/g' .zshrc
  ```

- Replace **case-insensitive** **old** with **new** on all lines and print to stdout:
  ``` bash
  sed 's/old/new/gi' .zshrc
  ```

- Replace **old** with **OLD** on all lines using extended regex and print to stdout:
  ``` bash
  sed -E 's/(old)/\U\1/g' .bashrc
  command | sed -E 's/(old)/\U\1/g'
  ```

  > **NOTE**: `\U` convert to uppercase; `\1` tells it to convert the first capture group of the sed command (which is **old**).

- Replace **old** with **new** in-place in a file (writes to the file!):
  ``` bash
  sed -i 's/old/new/g' .zshrc
  ```

- Replace **old** with **new** and **first** with **second** in-place in a file (writes to the file!):
  ``` bash
  sed -i -e 's/old/new/g' -e 's/first/second/g' .bashrc
  ```

- Print the **first 10 lines** to stdout (similar to 'head'):
  ``` bash
  command | sed -n '10p'
  ```

  > NOTE The `-n` flag suppresses the printing of the entire output of the command.  Without the `-n`, it would print the 10 lines and then it would print the entire output from command.

- Print only lines that contain the pattern (similar to 'grep'):
  ``` bash
  sed -n '/pattern/p' /etc/apt/sources.list
  ```

- **Delete pattern** and print to stdout:
  ``` bash
  sed '/pattern/d' .zshrc
  ```

- **Delete lines 1-4 of a file** and **create a back up** file with the .bak extension:
  ``` bash
  sed -i.bak '1,4d' .zshrc
  ```

- **Delete blank lines** (with or without spaces/tabs) from a file and print to stdout:
  ``` bash
  sed '/^[[:space:]]*$/d' .zshrc
  ```

- **Insert a new line** at the **beginning** of file, overwriting the file in-place:
  ``` bash
  sed -i '1i\A new first line\' .bashrc
  ```

- Inserting a line before a pattern and print to stdout.
  ``` bash
  sed '/pattern/i\This is a new line' .bashrc
  ```

- Append a line after a pattern and print to stdout.
  ``` bash
  sed '/pattern/a\This is a new line' .bashrc
  ```

## I/O redirection

Redirection is a process where we can copy the output of any command(s), file(s) into a new file.There are two ways of redirecting the output into a file.
Using `>` or `>> filename` after the command.
- Create a file named devops.txt with below content.
- Search for text "tech" replace it with "tools" and redirect output to a new file.

``` bash
sed 's/tech/tools/g' devops.txt > newtools.txt
```
> **note**: if the given name of the file is not available a new file will be created automatically. If the file already exists then it will #overwrite# contents of that file.

- Appending another output in same file with `>>` .
  ``` bash
  tail /etc/passwd >> newtools.txt
  ```

- Redirecting only error to a file `2>>`.
  ``` bash
  uptimer 2>> /tmp/error.log
  ```

- Redirecting all the output to a file `&>>`.
  ``` bash
  uptimer &>> /tmp/error.log
  ```

## Piping

So far we've dealt with sending data to and from files. Now we'll take a look at a mechanism for sending data from one program to another. It's called piping and the operator we use is ( | ). What this operator does is feed the output from the program on the left as input to the program on the right.
``` bash
$ ls | head -3
$ ls | grep logdir
$ cat /etc/passwd | grep root
```

## Find

**find** command is used to find the files or directory's path, it is exactly like the find option in windows where you can search for a file

| Options | Usage                                      |
|---------|--------------------------------------------|
| -name   | search a file with its name                |
| -inum   | search a file with particular inode number |
| -type   | search a particular type of file           |
| -user   | for files whose owner is a particular user |
| -group  | for files belonging to particular group    |

## Users & Groups
### USERS
#### Some important points related to Users:
- users and groups are used to control access to files and resources
- users login to the system by supplying their usernames and passwords
- every file on the system is owned by a user and associated with a group
- every process has an owner and group affiliation and can only access the resources its owner or group can access
- every user of the system is assigned a unique user ID number (the #UID#)
- user's names and UID are stored in _/etc/passwd_
- user's password is stored in _/etc/shadow_ in encrypted form
- users are assigned a #home directory# and a program that is run when they login (usually in a shell)
- users cannot read,write or execute each other's files without permission

### Types of user

| TYPE    | EXAMPLE          | USER  and GROUP ID (ID & GID) | HOME DIR     | SHELL         |
|---------|------------------|--------------------|--------------|---------------|
| ROOT    | root             | 0                  | /root        | /bin/bash     |
| REGULAR | Steve, vagrant   | 1000 to 60000      | /home/user   | /bin/bash     |
| SERVICE | ftp, ssh, apache | 1 to 999           | /var/ftp etc | /sbin/nologin |

There are three types of users in Linux:

| user | description |
|--|--|
| super user or root user | Super user or the root user is the most powerful user. He is the administrator user. |
| system user | These users are created by the softwares or applications. For example, if we install Apache it will create a user called apache. They are known as system users. |
| normal user | Normal users are the users created by root user. They are normal users like Musa, Ratul etc. |

> Only the root user has the permission to create or remove a normal user.

Whenever a user is created in Linux, the following things are created by default:
- A home directory (/home/username)
- unique ID and GID

## Passwd file
``` bash
 [root@linux ~]# head /etc/passwd
 root:x:0:0:root:/root:/bin/bash
 bin:x:1:1:bin:/bin:/sbin/nologin
```

The above field are
- `root` = name
- `x` = link to password file i.e. /etc/shadow
- `0` or `1` = UID (user id)
- `0` or `1` = GID (group id)
- `root` or `bin` = comment (brief information about the user)
- `/root` or `/bin` = home directory of the user
- `/bin/bash` or `/sbin/nologin` = shell

## Group file
### /etc/group

The file <u>/etc/group</u> stores group information. Each line in this file stores one group entry.
``` bash
Group name, group password, GID, group members
```

``` bash
[root@localhost ~]# head /etc/group
root:x:0:
bin:x:1:
daemon:x:2:
```

### ADD USER, SET PASSWORD & SWITCH TO USER

add user
``` bash
sudo useradd rahul
```

set a password for the user
``` bash
sudo passwd rahul
```

switch to the user
``` bash
su - rahul
```

see all the important information of the user
``` bash
id
```

### ADD USER, GROUP & USER INTO GROUP
- create an user
  ``` bash
  $ useradd devops
  $ id devops
  $ grep devops /etc/passwd
  ```
 
- add the user to the group
  ``` bash
  $ groupadd opsadmin
  $ usermod -aG opsadmin devops
  $ grep opsadmin /etc/group
  $ id devops
  ```

### DELETE USER & GROUP
``` bash
$ sudo userdel -r rahul
$ sudo groupdel opsadmin
$ sudo id rahul
```

## The `/etc/shadow` file

This file stores users' password and password related information. Just like /etc/passwd file, this file also uses an individual line for each entry.
1. Username
2. Encrypted password
3. Number of days when password was last changed
4. Number of days before password can be changed
5. Number of days after password must be changed
6. Number of days before password expiry date to display the warning message
7. Number of days to disable the account after the password expiry
8. Number of days since the account is disabled
9. Reserved field

Check it out!
``` bash
cat /etc/shadow
```

## USER & GROUP cheatsheet

| COMMANDS                   | DESCRIPTION                |
|----------------------------|----------------------------|
| useradd                    | Creates user in RedHat     |
| adduser                    | Creates user in ubuntu     |
| id                         | Shows user info            |
| groupadd                   | Creates group              |
| usermod -G grpname usrname | Adds user to group         |
| passw                      | set/reset password         |
| userdel -r                 | removes user with home dir |
| groupdel                   | removes group              |
| last                       | shows last login in system |
| who                        | who is logged into system  |
| whoami                     | username                   |
| lsof -u user               | List files opened by user  |

# File permissions
## viewing permissions from CLI
File permissions may be viewed by this:
``` bash
ls -l
```

Four symbols are used when displaying permissions:

| symbol | description                                                     |
|--------|-----------------------------------------------------------------|
| r      | read permission of a file or list a folder's contents           |
| w      | write permission of a file or remove and make files in a folder |
| x      | execute permission of a program                                 |
| -      | no permission                                                   |

## change file ownership
- only root can change a file's owner
- only root or the owner can change a file's group
- ownership is changed with #chown#:
  ``` bash
  chown -R user_name file|directory
  ```

- group ownership is changed with #chgrp#:
  ``` bash
  chgrp -R group_name file|directory
  ```

## Changing Permissions - Symbolic Method
- To change access modes:
  ``` bash
  chmod [-OPTION] ... mode[,mode] filel directory ...
  ```
- mode includes:
  - `u`, `g` or `o` for user, group and other
  - `+`, `-` or `=` for grant, deny or set
  - `r`, `w` or `x` for read, write and execute

- Options include:

| options     | descriptions                        |
|-------------|-------------------------------------|
| -R          | Recursive                           |
| -v          | verbose                             |
| --reference | reference another file for its mode |

- Examples:

Grant read access to all for file
``` bash  
chmod ugo+r file
```

Deny write and execute to others for /dir/
``` bash  
chmod o-wx dir
```

## Changing Permissions - Numeric Method

- Uses a three-digit mode number
  - first digit specifies owner 's permissions
  - second digit specifies group permissions
  - third digit represents others' permissions
- Permissions are calculated by adding:
  - 4 (for read)
  - 2 (for write)
  - 1 (for execute)
    
*Example*:
``` bash
chmod 640 myfile
```

## Sudo

sudo gives power to a normal user to execute commands which is owned by root user. Example shown below:
``` bash
sudo -i
```

The above command changes normal user to root user

> **note**: If a user has already full sudoers privilege, it can become a root user anytime.

## Adding user sam in sudoers list.
``` bash
$ sudo -i
> export EDITOR=nvim
> visudo
```

Add another line:
``` bash
steve    ALL=(ALL:ALL) ALL
```

Like a user a group can also be added into sudoers list.
``` bash
%admin    ALL=(ALL:ALL) ALL
```

Every time you enter sudo command it asks your own password. To turn that off use NOPASSWD in sudoers file.
``` bash
sam    ALL=(ALL:ALL) NOPASSWD: ALL
```

Changing to any other user with `su -` command.
``` bash
su - sam
```

Become a root user from sam user login.
``` bash
sudo -i
```

# Software Management
## Download package from internet
### CentOS
   To install Tree
``` bash   
$ curl "https://rpmfind.net/linux/centos/7.9.2009/os/x86_64/Packages/tree-1.6.0-10.el7.x86_64.rpm" -o "tree-1.6.0-10.el7.x86_64.rpm"
$ sudo rpm -ivh tree-1.6.0-10.wl7.x86_64.rmp 
```

> **note**: Due to Dependencies its failing and it will be installed one we install all the dependencies. But what if we have Hundreds of dependencies, And that can be solved easily by other package managers like `yum`.

> <u>repos.d/</u> directory: It reads each YUM Repository configuration file to get the information required to download and install new software, resolves software dependencies and installs the required RPM package files.

YUM Repository configuration files must: be located in _/etc/yum.repos.d_
``` bash
ls /etc/yum.repos.d
```

#### yum commands

| command                    | description                       |
|----------------------------|-----------------------------------|
| yum --help                 | Show the help                     |
| yum search <pkg>           | Search from repositories          |
| yum install <pkg> -y       | Install a packae                  |
| yum reinstall <pkg>        | Reinstall a packae                |
| yum remove <pkg>           | Install a packae                  |
| yum update                 | Update all packages               |
| yum update <pkg>           | Update only a package             |
| yum grouplist              | List all available group packages |
| yum groupinstall <grpname> | Install all packages in a group   |
| yum repolist               | List enabled dnf repositories     |
| yum clean all              | Clean dnf cache                   |
| yum install epel-release   | Activate an additional repository |
| yum history                | View history of dnf               |
| yum info <pkg>             | Show package information          |

#### rpm commands

| command                | description                          |
|------------------------|--------------------------------------|
| rpm -ivh <rpm-file>    | Install the package                  |
| rpm -Uvh <rpm-file>    | Upgrade package                      |
| rpm -ev <pkg>          | Erase/remove a package               |
| rpm -ev --nodeps <pkg> | Remove without checking dependencies |
| rpm -qa                | List all installed packages          |
| rpm -qi <pkg>          | Display information with description |
| rpm -qf <file_path>    | Find what package a file belongs to  |
| rpm -qc <pkg>          | Display conf file for a package      |
| rpm -qcf <file_path>   | Display conf file for a command      |
| rpm -qa --last         | List of all recently installed RPMs  |
| rpm -qpR <file>        | Show dependencies of the program     |
| rpm -qR  <pkg>         | Show dependencies of the program     |

#### dnf commands

| command                    | description                       |
|----------------------------|-----------------------------------|
| dnf --help                 | Show the help                     |
| dnf search <pkg>           | Search from repositories          |
| dnf install <pkg> -y       | Install a packae                  |
| dnf reinstall <pkg>        | Reinstall a packae                |
| dnf remove <pkg>           | Install a packae                  |
| dnf update                 | Update all packages               |
| dnf update <pkg>           | Update only a package             |
| dnf grouplist              | List all available group packages |
| dnf groupinstall <grpname> | Install all packages in a group   |
| dnf repolist               | List enabled dnf repositories     |
| dnf clean all              | Clean dnf cache                   |
| dnf install epel-release   | Activate an additional repository |
| dnf history                | View history of dnf               |
| dnf info <pkg>             | Show package information          |

### Ubuntu
   To install Tree
``` bash   
$ wget "http://archive.ubuntu.com/ubuntu/pool/universe/t/tree/tree_1.7.0-3_amd64.deb" -o tree_1.7.0-3_amd64.deb
$ sudo dpkg -i tree_1.7.0-3_amd64.deb
```

We have seen `yum` Like that for Ubuntu we have a package manager `apt`.

The <u>sources.list</u> file is a key factor in adding or upgrading applications to your Ubuntu installation. This is also used by your system for system updates. The file is basically the roadmap for your system to know where it may download programs for installation or upgrade.

``` bash
cat /etc/apt/sources.list
```

#### apt commands

| command                    | description                       |
|----------------------------|-----------------------------------|
| apt --help                 | Show the help                     |
| apt search <pkg>           | Search from repositories          |
| apt install <pkg> -y       | Install a packae                  |
| apt reinstall <pkg>        | Reinstall a packae                |
| apt remove <pkg>           | Install a packae                  |
| apt update                 | Update all packages               |
| apt update <pkg>           | Update only a package             |
| apt grouplist              | List all available group packages |
| apt groupinstall <grpname> | Install all packages in a group   |
| apt repolist               | List enabled dnf repositories     |
| apt clean all              | Clean dnf cache                   |
| apt history                | View history of dnf               |
| apt show <pkg>             | Show package information          |

# Other commands
## service commands

| commands                         | description                     |
|--|--|
| sudo systemctl start <service>   | starts the service              |
| sudo systemctl stop <service>    | stops the service               |
| sudo systemctl restart <service> | restarts the service            |
| systemctl status <service>       | show the service status         |
| sudo systemctl reload <service>  | reload conf                     |
| sudo systemctl enable <service>  | starts the service at boot time |
| sudo systemctl disable <service> | stops the service at boot time  |
| systemctl is-active <service>    | whether the service is active   |
| systemctl is-enabled <service>   | whether the service is enabled  |

## archive commands
### tar
archive your files by this command:
``` bash
tar -czvf com.tar.gz docs # docs is the folder we will archive
```
Here,
- `-c` means create an archive
- `-z` means use gzip for archiving
- `-v` means verbose
- `-f` means file

> **note**: If you don't understand what is the type of a particular file, you can use #file# command.
``` bash
  file mytxt
```

to extract an archive, use this command:
``` bash
tar -xzvf com.tar.gz
```

Here,
`-x` means extract the archive

> **note**: You can choose your destination path of extract using #-C# command.
``` bash
tar -xzvf com.tar.gz -C /opt/
```

For details about tar, use this command:
``` bash
tar --help
```

### zip

First we need to install them:
``` bash
sudo apt install -y zip unzip
```

zip your files:
``` bash
zip -r Downloads.zip Downloads
```

unzip your files:
``` bash
unzip Downloads.zip
```

## Process monitor
Processes are running programs either in foreground or background. Two softwares are used to monitor the processes:

### top
Top is already installed in almost all Linux distros. Just open a terminal and type:
``` bash
top
```

The first line contains:
- Clock
- Uptime
- no of users logged in
- load average of 1, 5 and 15 minutes accordingly

Second line contains information about #tasks#:
- Total tasks
- Running tasks
- Sleeping tasks
- Deep sleeping tasks
- stopped tasks
- zombie tasks

> **note**: top considers processes as tasks

Third line contains infrmation about **CPU usage**:
- amount of time running user processes
- amount of time running system processes
- amount of time running niced processes
- kernel idle handler
- time waiting for I/O
- time spent for hardware interrupts
- time spent for software interrupts
- time stolen by hypervisiors

Fourth line is about **memory usage**.  
Fifth line is about **swap usage**.
- last portion indicates memory available for new process without swap

The bottom portion of top is the process table.
- more processes can be seen by up and down arrow keys
   
> **note**: list gets refreshed every 3 seconds. To increase delay type -d . Suppose we need 10 seconds delay, then:  -d 10

The table contains following columns:
 - Process ID (PID)
 - User that started the process
 - priority number
 - nice value (-19 to 20) higher the value nicer you are! meaning giving other processes giving priority over that process
 - total virtual memory used by the task
 - non swap physical memory a task is using
 - shared memory size
 - status:
   - `R` - running
   - `S` - sleeping
   - `I` - idle
   - `T` - stopped
   - `Z` - zombie
 - % of CPU used within the last refresh period.
   _note_: No of CPUs = No of percentage, for example 4 CPU means 400%
 - % of physical memory used
 - total CPU time a process has used
 - name of the running program. Type #C# to see the full program name.

| keybinding | actions                            |
|------------|------------------------------------|
| z          | enables color                      |
| 1          | total CPUs or individual CPU       |
| t          | CPU usage display change           |
| m          | Memory usage display change        |
| c          | program name or total program path |
| x          | highlight sort field               |
| b          | toggle bold and reverse mode       |
| <, >       | change the sort field              |
| R          | reverse the sort order             |
| L          | locate a string                    |
| u          | filter by username                 |
| o          | filter by other                    |
| V          | tree view                          |
| k          | kill a process                     |
| h          | help                               |

_note_: Display modes are text, bar, graph, block graph, none
o COMMAND=dd shows the commands that have "dd" in it

## htop

First we need to install the software.
``` bash
sudo apt install htop # for debian and its derivatives
```

htop can easily be controlled by mouse clicks!

## ps

show all the processes
``` bash
ps aux
```

process that have "brave" in it
``` bash
ps aux | grep -i "brave"
```

kill a process
``` bash
kill <PID>
```

see all the commands you have run so far
``` bash
history
```
