## Why using the command-line?

This question is very simple to answer, because the command-line (shell) is old as computers. Most programs on Linux can also be controlled by command-line without any graphical user interface (GUI). This makes the command-line as the most powerful tool on a computer, especially for servers, because they don't need a display and there are also many programs, which will never provide any GUI, for example databases. For Linux-Servers it is the best way to access your server remotly over a SSH-Connection (Secure Shell). The data-transfer from your computer to the server is very fast and easy.

The following section gives an overview about the most used Linux-Commands, please add more, if something important is missing.


### General

When you type a command, there are some essential elements you have to know. Here is a simple example for a command on the command-line:

```bash
node server.js | bunyan --mongodb
```

This command contains 3 parts:

1. `node server.js` starts your node-application and it has to know, which file contains your node-application. The command above would already work without the rest, but the following parameters are specifing and configurating the command/program in a better way.
2. With the so called **Pipe-Operator** (`|`) the program starts the node-application with a logger in the background. It is not necessary to use it, but nice to know that there is a Pipe-Operator. (More information can be found [here](https://wiki.ubuntuusers.de/Shell/Umleitungen/)).
3. With the so called **Flag**, you can specify a parameter or a setting, which is very often used. In this case, we want to specify, that the node-application, should connect to a Mongo-Database. It is also possible to change this flag to `--redis` or with a shortcut `-r` (same as `--redis`). If the program recoginze this flag, then it can switch for example the database of you choice. We will use this in our nodejs-application with the help of the node-commander-package.

**Attention:**<br>
If you don't know which parameters can be used in a command, the programs give you an overview about all flags and parameters. You can get this list by typing `--help` or `-h`.

### ROOT-User

The root-user is a super-user and have the right to change any file on the system, even the system-files. You need this user mostly, if you want to install something on the system. For example if you want to update the Ubuntu OS, it is not working without the sudo-command (expect you are an admin and have root-rights for your user-account). Try the following:
`apt-get update` and then try `sudo apt-get update`.
It is also possible to change to the root-user by the following command `sudo su` and then run the command `apt-get update`.


### Overview

| Command | Use | Example |
|---------|-----|---------|
| `ssh <URL>` | | `ssh 192.168.178.1` |
| `ssh <USER>@<URL/IP>` | | `ssh pi@192.168.178.1` |
| `ssh <USER>@<URL/IP> -p <PORT>` | | `ssh pi@192.168.178.1 -p 22` |
| `ls` | list files of current folder | |
| `ls -l` | list files of current folder, but as a list | |
| `ls -a` | list all files of current folders, as well as hided files, for example (`.gitignore`) | |
| `cd` | change directory | `cd /home` |
| `cd ../` | change directory | `cd /home` |
| `cd ~` | change to home directory of logged-in user |
| | | | 
| `mkdir` | create directory | `mkdir new-folder` |
| `mv <FILE-NAME> <NEW-FILE-NAME> ` | rename a file or move file to other folder (e.g. `new-folder`) | `mv oldname.txt new-folder/newname.txt` |
| `rm <FILE-NAME>` | remove a file or an empty folder, it is not working with a folder, which contains other files (see next command ) | `rm file.txt` |
| `rm -rf <FOLDER-NAME>` | remove a file or folder, which contains other files | `rm -rf new` |
| `sudo su` | change to root user | |
| `exit` | logout of the current user, also possible for the root-user | |
| `sudo nano <FILE>` | | |
| `sudo nano /etc/crontab` | | |
| `apt-get update` | | |
| `apt-get install <PACKAGE>` | | |


### Useful links

* [https://wiki.ubuntuusers.de/Shell](https://wiki.ubuntuusers.de/Shell) (only German)
* [http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php) (English)


