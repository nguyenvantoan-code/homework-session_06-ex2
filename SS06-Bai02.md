root@103725795523314:~# groupadd devops-admin
root@103725795523314:~# getent group devops-admin
devops-admin:x:1006:
root@103725795523314:~# adduser deployer
info: Adding user `deployer' ...
info: Selecting UID/GID from range 1000 to 59999 ...
info: Adding new group `deployer' (1007) ...
info: Adding new user `deployer' (1007) with group `deployer (1007)' ...
info: Creating home directory `/home/deployer' ...
info: Copying files from `/etc/skel' ...
New password:
Retype new password:
passwd: password updated successfully
Changing the user information for deployer
Enter the new value, or press ENTER for the default
        Full Name []:
        Room Number []:
        Work Phone []:
        Home Phone []:
        Other []:
Is the information correct? [Y/n] Y
info: Adding new user `deployer' to supplemental / extra groups `users' ...
info: Adding user `deployer' to group `users' ...
root@103725795523314:~# usermod -aG devops-admin deployer
root@103725795523314:~# id depkoyer
id: ‘depkoyer’: no such user
root@103725795523314:~# id deployer
uid=1007(deployer) gid=1007(deployer) groups=1007(deployer),100(users),1006(devops-admin)
root@103725795523314:~# visudo
root@103725795523314:~# xong
Command 'xong' not found, did you mean:
  command 'kong' from snap kong (2.0.4)
  command 'kong' from snap kong (0.13.1)
See 'snap info <snapname>' for additional versions.
root@103725795523314:~# su - deloyer
su: user deloyer does not exist or the user entry does not contain all the required fields
root@103725795523314:~# su - deployer
deployer@103725795523314:~$ whoami
deployer
deployer@103725795523314:~$ sudo -1
sudo: invalid option -- '1'
usage: sudo -h | -K | -k | -V
usage: sudo -v [-ABkNnS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-ABkNnS] [-g group] [-h host] [-p prompt] [-U user]
            [-u user] [command [arg ...]]
usage: sudo [-ABbEHkNnPS] [-r role] [-t type] [-C num] [-D directory]
            [-g group] [-h host] [-p prompt] [-R directory] [-T timeout]
            [-u user] [VAR=value] [-i | -s] [command [arg ...]]
usage: sudo -e [-ABkNnS] [-r role] [-t type] [-C num] [-D directory]
            [-g group] [-h host] [-p prompt] [-R directory] [-T timeout]
            [-u user] file ...
deployer@103725795523314:~$ sudo -l
Matching Defaults entries for deployer on 103725795523314:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin,
    use_pty

User deployer may run the following commands on 103725795523314:
    (ALL) NOPASSWD: /usr/bin/systemctl start *, /usr/bin/systemctl stop *,
        /usr/bin/systemctl restart *, /usr/bin/systemctl status *
deployer@103725795523314:~$ sudo systemctl restart cron
deployer@103725795523314:~$ sudo systemctl status cron
● cron.service - Regular background program processing daemon
     Loaded: loaded (/usr/lib/systemd/system/cron.service; enabled; preset: ena>
     Active: active (running) since Wed 2026-10-07 14:33:07 BST; 19s ago
       Docs: man:cron(8)
   Main PID: 220364 (cron)
      Tasks: 1 (limit: 4556)
     Memory: 352.0K (peak: 804.0K)
        CPU: 9ms
     CGroup: /system.slice/cron.service
             └─220364 /usr/sbin/cron -f -P

Oct 07 14:33:07 103725795523314 systemd[1]: Started cron.service - Regular back>
Oct 07 14:33:07 103725795523314 (cron)[220364]: cron.service: Referenced but un>
Oct 07 14:33:07 103725795523314 cron[220364]: (CRON) INFO (pidfile fd = 3)
Oct 07 14:33:07 103725795523314 cron[220364]: (CRON) INFO (Skipping @reboot job>
