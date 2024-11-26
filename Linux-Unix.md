## alias
Used to create alias/short form for commonly used commands

Create a alias k for kubectl 
```
alias k='kubectl'
```
Create an alias gl for git log
```
alias gl='git log --oneline --graph --decorate --all'
```


## Awk
Used for processing file having tabular data

#### Printing file
`Awk '{print}' <file_name>`

#### Printing first column
`Awk '{print 1$}' <file_name>`

#### Print fist and second column
`Print 1$ 2$`

#### Print fist and second column sperated by space
`Print 1$,2$`

#### Print last column
`print  $NF`

#### Print second last column
`Print $(NF-1)`
#### Second row alone
`NR==2 {print $0}`
#### Second to fifth rows
`NR==2,NR==5 {print $0}`
#### Second and fifth rows
`NR==2;NR==5 {print $0}`
#### File with separator ;
`Awk -F ";" '{print $1}' <file_name>`
#### Filter rows having some string
`Awk '/<string>/ {print }' <file_name>`
#### Filter rows having string1 or string2
`Awk '/<string1>|<string2>/ {}' <file_name>`
#### Filter rows for string in second column
`awk '$2~/<str>/ {}' <file_name>`
#### Filter rows where 4th column is same as 5th column
`awk '$4==$5 {print }' <file_name>`




## Cat
#### Read a file
`cat /var/www/html/index.html`
#### Can be used for contacting file
`Cat 1.txt 2.txt > 3.txt`

## chage
Used to set expriry date for account or password for local users
#### List user account aging information
`chage -l <uid>`
#### Change the password expiration validity days
`chage -M 90 <uid>`
#### Change the last password change date
`chage -d $(date  +%Y-%m-%d) <uid>`
#### Change the account expiration date
`chage -E $(date -d  +90days +%Y-%m-%d) <uid>`

## Chgrp
#### Change owner group
`Sudo chgrp _guest <file_name>`
#### Changing owner group for a directory
`Sudo chgrp -R <group_name> <dir>`

## Chmod
Used change the permission of the file
`Chmod u=rwx <file_name>`
u - owner, g - group, o - others

#### Add executable permission to all
`Chmod +x <file_name>`
#### To remove executable permission from all
`Chmod -x <file_name>`



## Chown
#### Change ownership of a file
`Sudo chown whoami <file_name>`
#### Changing owner for a directory
`Sudo chown -R <user_name> <dir>`
`chown -R <uid>:<gid> <dir>`

## cp
Copy utility
```
cp ./test.txt         /tmp           # file copy
cp -r ./bin           /tmp           # directory copy
cp -r {./bin,./lib}   /tmp           # copy multiple directory
```

## Crontab
Schedule
```
Crontab -e.   > Edit
Crontab -l.    > List
```

## Curl
Load what is available in the url
```
curl localhost:80
```

Download a file
```
curl ftp://localhost:80/a.tar.gz -o /TMP/a.tar.gz
```

## df
Disk free used to display the statistic about the amount of free space on the specified file system
```
df
df -h    #Data in human readable form
```

## dhclient
Refresh DHCP option parameter
```
sudo dhclient -r eth0
```

## dig
#### Dig command is similar to nslookup in windows
`dig +nocmd test.example.com A`

## Echo
Echo is used to display/print text, variable.. etc

Writing index html to apache home dir
echo "Hello world from $(hostname -f)" > /var/www/html/index.html 

Get variable value
myvar=123
`echo "$myvar"`
`echo ${myvar}`
Variable can be a command
mycmd=ls
$mycmd
Environmental variables
USER
HOME
PATH
Settings output of command to a variable
d=$(ls)
Another form of command substitution
echo "`date`"
echo "$(date)"

## Firewall
Installing firewall into CentOS, starting the service and enabling into system configuration to get it started automatically when system restart.

`sudo yum install -y firewalld`
`sudo service firewalld start`
`sudo systemctl enable firewalld`

Opening firewall for mariadb and refreshing firewall to take changes in effect
`sudo firewall-cmd --permanent --zone=public --add-port=3306/tcp`
`sudo firewall-cmd --reload`


## File
To view the information of file system on device
`file -s /dev/xvdb`
To list details of a file
`File <path>`

## Find
#### Used to find file with specific name or type
`Find -name *.TXT`
#### Find all files
`Find .`
#### Find all directory
`Find -filetype d`

## Grep
#### Used for searching text in files
```
Grep so <path>
```
#### Search text case insensitive
```
Grep -i so <path>
```
#### Search for line without a text
```
Grep -v so <path>
```
#### Search for text in all files in directory
```
grep -r <txt>
```
### Search a text and display lines before and after the match
```
grep -B 3 -A 2 foo README.txt
# same number for lines before and after
grep -C 3 foo README.txt
```

## id
Details of the ID currently logged in
```
id
uid=1001(ssm-user) gid=1001(ssm-user) group=1001(ssm-user) context=system_u: system_r:unconfined_service_t:s0
```
List the group of current user
```
id -Gn
```

## Ifconfig 
Similar to ipconfig in windows
`ifconfig -a`

## Init 6
Reboot Linux machine

## Killall / kill / pkill
Kills the process
`Killall <process_name>`
`Kill <pid>`
`Kill -9 <pid>`
`pkill <process_name>`

## Ln
Linked file
`ln -s /opt/tomcat/bin/startup.sh /usr/local/bin/tomcatup`


## Logon script
Login scripts are run when you start shell. Its present in home folder
.profile/.bashrc/.bash_profile/.login
.profile   - mac and Mainframe
.bashrc - ubuntu
To load the environment variable update now
`Source .profile`

## Ls
List directory
`Ls <path>`
-a list hidden files
-l list in long format
List detail of last 4 file
`ls -l | tail -4`

## Lsof
List open file
`lsof <file_name>`

## Lsblk
Display all Mount volume and Mount point
`lsblk`

## Mkdir
Create directory
`mkdir`

## Mkfs
Making the file system ready(format) for Mount
`sudo mkfs -t ext4 <device_name>`

## Mount
_Mount an EFS_ \
`Sudo Mount -t EFS <ipaddress>:/ </directory>` \
`sudo mount <device_name> <mount_point>` \
_Permanent Mount_ \
`sudo vi /etc/fstab` \
_Mount device based on fstab_ \
`sudo mount -a` \
  

_List Mount_ \
`df -h` \

## Nano
It's a file editor with UI
`Nano <file_name>`

## NC
Netcat is used start listener
`nc -l -p 81`

## Netstat
To check if listener is running on a port number
`Netstat -anlp | grep <port_nr>`
To display listener running
`netstat -plnt`

## Open/xdg-open
Open file in default 

## PS
List the process running

`ps aux`
`sudo ps -a`
`ps aux | grep nginx`

## PWD
Present working directory
`PWD`

## Read
Read  data from user
`read var`
`read -p "enter data:" data`
`read -s password`
`read -sp "enter password" pwd`


## RM
Delete
`rm <filename>`
Deleting directory
`rm -r <dir_name>

## Service
To check the status of a service e.g. firewalld
`Service firewalld status`

## Sleep
Used to pause the execution for some time
`Sleep 1`     - 1 sec
`Sleep 0.5`  - .5 sec

## SSH
SSH
`SSH -i <key.pem> ec2-user@<ip-address>`

SSH-keygen
`ssh-keygen -t rsa -b 2048 -C "aws-code-commit"`

Create config file in .ssh dir, and add below text
Host git-codecommit.*.amazonaws.com
  User <>
  Identity file ~/.ssh/aws-code-commit


## Start
Start apache service and keep starting after reboot
`systemctl start httpd.service`
`systemstl enable httpd.service`

## Sudo
Root Access
`Sudo su -`
Run command with root user
`Sudu <command>`
Running shell with root access, all command will be run with root access
`Sudo bash`

## Systemctl
This is used to start, enable and enquire status of a service

`sudo systemctl start mariadb`
`sudo systemctl enable mariadb`
`sudo systemctl status mariadb`


## Tar
Extracting a zip file
`tar –xf Python-3.8.3.tgz`

## Top
Command to list the top consumer of memory or CPU. Similar to task manager.
`top`
`sudo top`

## Touch
To create a file in PWD
`touch <file_name>`

## Unset
Unset any variable
`unset <var>`

## Wget
Download a file
`wget https://www.python.org/ftp/python/3.7.5/Python-3.7.5.tgz`


## Which
Is used get location of the command
`Which <command>`

## Whoami
Gives the current user name
`Whoami`

## xargs 
xargs is a Unix command which can be used to build and execute commands from standard input. 
```
kubectl get po | grep test | cut -d ' ' -f 1 | xargs kubectl logs
echo 'file1 file2 file3 file4' | xargs touch
```
prompt for input
```
echo 'file1a file2a file3a file4a' | xargs -p touch
```
take input from file
```
echo 'file1a file2a file3a file4a' > input.txt
xargs -a input.txt rm
```

## yum
yum is a package manager in redhat based linux distros

Update all the installed applications
`yum update -y`
Install apache
`yum install -y https.x86_64`

Installing NFS client on Linux
`sudo yum install -y amazon-efs-utils.`

For RedHat or SUSE Linux
`sudo yum install -y nfs-utils.`

Installting local rpm file
`yum localinstall <path to rpm file>`

For Ubuntu
`Sudo apt-get install nfs-common`



## Operators
. PWD  
.. one folder up  
~ home  
> Redirecting output to a file  
>> Redirecting output to a file append  
| Pipe is used to run command on output of other command  
+-*/ plus minus multiplication division  
% reminder  
** Power  
Var++ add 1 after running this  
++Var add 1 before running  
+=,-= short hand  
$(<command>) command expansion  
`<command>` command expansion  
$((<arithmetic_exp>)) arithmetic expansion  
Executing shell script in current directory  
./<script_file>  
Shell start with shebang  
#!<location_of_program>  
#!/bin/bash

## Inputs to script or function
$# - Number of inputs  
$@ - All the inputs  
$1 - First input  
$0 - name of the script  
$? - return code of last operation  

## Condition Check
### Simple if statement
```
if [ 3 -eq 3 ] ;  then
<command>
fi
```

### If else statement
```
if [<condition>]; then
<Command>
else
<Command>
fi
```

### If elif and else
```
if [<condition>]; then
<Command>
elif [<condition>]; then
<Command>
elif [<condition>]; then
<Command>
else
<Command>
fi
```

### case statement
```
case $choise in
1)
echo " You choose A"
;;
2)
echo " You choose B"
;;
*)
echo "none of the above"
esac
```

### Nested case
```
OS=$(uname -s | tr A-Z a-z)

case $OS in
  linux)
    source /etc/os-release
    case $ID in
      debian|ubuntu|mint)
        sudo apt-get install jq -y
        ;;

      fedora|rhel|centos|amzn)
        sudo dnf install jq -y
        ;;

      *)
        if [[ $(uname -p) == "x86_64" ]]; then
          platform=amd64
        else 
          platform=arm64
        fi    
        curl https://github.com/jqlang/jq/releases/download/jq-1.7.1/jq-linux-${platform} -o jq
        sudo mv jq /usr/local/bin
        sudo chmod +x /usr/local/bin
        ;;
    esac
  ;;

  darwin)
    brew install jq
  ;;

  *)
    echo -n "unsupported OS"
    ;;
esac
```

```
Any number b/w 0 9 [0-9]
Any upper case [A-Z]
Any lower case [a-z]
```

### conditions For number
```
-eq  =
-ne <>
-gt >
-lt <
-ge >=
-le <=
```

### For string
```
==
!=
if [-z "$str"] empty string check
```

### For files
```
if [ -e <file>] existence check
!-e not existence
-d directory check
-r readable
-w writeable
-x executable
-s empty check
-f regular file and it should exist
```

## Loops
### for loop
```
for I in {1,2,3,4} 
do
echo "line"
done
```
{1..7} / {1,"hello",2,"bye"}

break - to break the loop

Running loop on all the files in PWD
```
for I in ./*
do
echo "name of file is : $i"
done
```

### While loop
```
while [ $number -le 15 ];
do
echo "number is $number"
number=$((number +4))
done
```

## Logical operators
```
-o  OR
-a  AND
```

## Function
```
mydate() {
echo $1
return 35
}

mydate "hello"
echo "return vale $?"
```

## Variable
Variable are global in nature
local var1=value      is local in function


exit - termination of script

$? - exit status

## File Test
-b filename - Block special file  
-c filename - Special character file  
-d directoryname - Check for directory Existence  
-e filename - Check for file existence, regardless of type (node, directory, socket, etc.)  
-f filename - Check for regular file existence not a directory  
-G filename - Check if file exists and is owned by effective group ID  
-G filename set-group-id - True if file exists and is set-group-id  
-k filename - Sticky bit  
-L filename - Symbolic link  
-O filename - True if file exists and is owned by the effective user id  
-r filename - Check if file is a readable  
-S filename - Check if file is socket  
-s filename - Check if file is nonzero size  
-u filename - Check if file set-user-id bit is set  
-w filename - Check if file is writable  
-x filename - Check if file is executable  
```
#!/bin/bash
file=./file
if [ ! -e "$file" ]; then
    echo "File does not exist"
else 
    echo "File exists"
fi
```

## File
- /etc/passwd
  File is used for authentication of user
  usermod or useradd is used to modify or add a user
  Format of the file
  <username>:<password>:<UID>:<GID>:<full_name>:<home_dir>:<login_shell>



## Networking Commands

