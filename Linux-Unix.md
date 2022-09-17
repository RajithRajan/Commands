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

Print second last column
Print $(NF-1)
Second row alone
'NR==2 {print $0}'
Second to fifth rows
'NR==2,NR==5 {print $0}'
Second and fifth rows
NR==2;NR==5 {print $0}'
File with separator ;
Awk -F ";" '{print $1}' <file_name>
Filter rows having some string
Awk '/<string>/ {print }' <file_name>
Filter rows having string1 or string2
Awk '/<string1>|<string2>/ {}' <file_name>
Filter rows for string in second column
awk '$2~/<str>/ {}' <file_name>
Filter rows where 4th column is same as 5th column
`awk '$4==$5 {print }' <file_name>`




## Cat
Read a file
cat /var/www/html/index.html
Can be used for contacting file
Cat 1.txt 2.txt > 3.txt

## chage
Used to set expriry date for account or password for local users
List user account aging information
chage -l <uid>
Change the password expiration validity days
chage -M 90 <uid>
Change the last password change date
chage -d $(date  +%Y-%m-%d) <uid>
Change the account expiration date
chage -E $(date -d  +90days +%Y-%m-%d) <uid>

## Chgrp
Change owner group
Sudo chgrp _guest <file_name>
Changing owner group for a directory
Sudo chgrp -R <group_name> <dir>

## Chmod
Top change the permission of the file
Chmod u=rwx <file_name>
u - owner, g - group, o - others

Add executable permission to all
Chmod +x <file_name>
To remove executable permission from all
Chmod -x <file_name>



## Chown
Change ownership of a file
Sudo chown whoami <file_name>
Changing owner for a directory
Sudo chown -R <user_name> <dir>
chown -R <uid>:<gid> <dir>

## Crontab
Schedule
Crontab -e.   > Edit
Crontab -l.    > List

## Curl
Load what is available in the url
curl localhost:80

Download a file
curl ftp://localhost:80/a.tar.gz -o /TMP/a.tar.gz

## Df
Disk free used to display the statistic about the amount of free space on the specified file system
df
df -h

## dig
Dig command is similar to nslookup in windows
dig +nocmd test.example.com A

## Echo
Echo is used to display text, variable.. etc

Writing index html to apache home dir
echo "Hello world from $(hostname -f)" > /var/www/html/index.html 

Get variable value
myvar=123
echo "$myvar"
echo ${myvar}
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

sudo yum install -y firewalld
sudo service firewalld start
sudo systemctl enable firewalld

Opening firewall for mariadb and refreshing firewall to take changes in effect
sudo firewall-cmd --permanent --zone=public --add-port=3306/tcp
sudo firewall-cmd --reload


## File
To view the information of file system on device
file -s /dev/xvdb
To list details of a file
File <path>

## Find
Used to find file with specific name or type
Find -name *.TXT
Find all files
Find .
Find all directory
Find -filetype d

## Grep
Used for searching text in files
Grep so <path>
Search text case insensitive
Grep -i so <path>
Search for line without a text
Grep -v so <path>

## id
Details of the ID currently logged in
id
uid=1001(ssm-user) gid=1001(ssm-user) group=1001(ssm-user) context=system_u: system_r:unconfined_service_t:s0

## Ifconfig 
Similar to ipconfig in windows
ifconfig -a

## Init 6
Reboot Linux machine

## Killall / kill / pkill
Kills the process
Killall <process_name>
Kill <pid>
Kill -9 <pid>
pkill <process_name>

## Ln
Linked file
ln -s /opt/tomcat/bin/startup.sh /usr/local/bin/tomcatup


## Logon script
Login scripts are run when you start shell. Its present in home folder
.profile/.bashrc/.bash_profile/.login
.profile   - mac and Mainframe
.bashrc - ubuntu
Source .profile

## Ls
List directory
Ls <path>
-a list hidden files
-l list in long format
List detail of last 4 file
ls -l | tail -4

## Lsof
List open file
lsof <file_name>

## Lsblk
Display all Mount volume and Mount point
lsblk

## Mkdir
Create directory
mkdir

## Mkfs
Making the file system ready(format) for Mount
sudo mkfs -t ext4 <device_name>

## Mount
Mount an EFS
Sudo Mount -t EFS <ipaddress>:/ </directory>
sudo mount <device_name> <mount_point>
Mount device based on fstab
sudo mount -a
Permanent Mount
vi /etc/fstab

List Mount
df -h

## Nano
It's a file editor with UI
Nano <file_name>

## NC
Netcat is used start listener
nc -l -p 81

## Netstat
To check if listener is running on a port number
Netstat -anlp | grep <port_nr>
To display listener running
netstat -plnt

## Open/xdg-open
Open file in default 

## PS
List the process running

ps aux
sudo ps -a
ps aux | grep nginx

## PWD
Present working directory
PWD

## Read
Read  data from user
read var
read -p "enter data:" data
read -s password
read -sp "enter password" pwd


## RM
Delete
rm

## Service
To check the status of a service e.g. firewalld
Service firewalld status

## Sleep
Used to pause the execution for some time
Sleep 1     - 1 sec
Sleep 0.5  - .5 sec

## SSH
SSH
SSH -i <key.pem> ec2-user@<ip-address>

SSH-keygen
ssh-keygen -t rsa -b 2048 -C "aws-code-commit"

Create config file in .ssh dir, and add below text
Host git-codecommit.*.amazonaws.com
  User <>
  Identity file ~/.ssh/aws-code-commit


## Start
Start apache service and keep starting after reboot
systemctl start httpd.service
systemstl enable httpd.service

## Sudo
Root Access
Sudo su -
Run command with root user
Sudu <command>
Running shell with root access, all command will be run with root access
Sudo bash

## Systemctl
This is used to start, enable and enquire status of a service

sudo systemctl start mariadb
sudo systemctl enable mariadb
sudo systemctl status mariadb


## Tar
Extracting a zip file
tar –xf Python-3.8.3.tgz

## Top
Command to list the top consumer of memory or CPU. Similar to task manager.
top
sudo top

## Touch
To create a file in PWD
touch <file_name>

## Unset
Unset any variable
unset <var>

## Wget
Download a file
wget https://www.python.org/ftp/python/3.7.5/Python-3.7.5.tgz


## Which
Is used get location of the command
Which <command>

## Whoami
Gives the current user name
Whoami

## Yum
Update all the installed applications
yum update -y
Install apache
yum install -y https.x86_64

Installing NFS client on Linux
sudo yum install -y amazon-efs-utils.

For RedHat or SUSE Linux
sudo yum install -y nfs-utils.

yum localinstall <path to rpm file>

For Ubuntu
Sudo apt-get install nfs-common



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

## Condition Check
if [ 3 -eq 3 ] ;  then
<command>
fi

if [<condition>]; then
<Command>
else
<Command>
fi

if [<condition>]; then
<Command>
elif [<condition>]; then
<Command>
elif [<condition>]; then
<Command>
else
<Command>
fi

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

Any number b/w 0 9 [0-9]
Any upper case [A-Z]
Any lower case [a-z]

For number
-eq  =
-ne <>
-gt >
-lt <
-ge >=
-le <=

For string
==
!=
if [-z "$str"] empty string check

For files
if [ -e <file>] existence check
!-e not existence
-d directory check
-r readable
-w writeable
-x executable
-s empty check
-f regular file and it should exist

Loops
for I in {1,2,3,4} 
do
echo "line"
done

{1..7} / {1,"hello",2,"bye"}

break - to break the loop

Running loop on all the files in PWD
for I in ./*
do
echo "name of file is : $i"
done

while [ $number -le 15 ];
do
echo "number is $number"
number=$((number +4))
done


## Logical operators
-o  OR
-a  AND

## Function
mydate() {
echo $1
return 35
}

mydate "hello"
echo "return vale $?"

Variable are global in nature
local var1=value      is local in function


exit - termination of script
$? - exit status



## File
/etc/passwd
File is used for authentication of user
usermod or useradd is used to modify or add a user

Format of the file
<username>:<password>:<UID>:<GID>:<full_name>:<home_dir>:<login_shell>



## Networking Commands

