### Env basics
```
uname -a  #Linux ubuntu 6.8.0-31-generic #31-Ubuntu SMP x86_64 GNU/Linux
cat /etc/os-release
lsb_release -a
```

### File Sanity
```
rtvk@rtvk-ThinkPad-E14-Gen-4:~$ mkdir Downloads/day_5.txt
rtvk@rtvk-ThinkPad-E14-Gen-4:~$ cp Downloads/day_5.txt/ Documents/
cp: -r not specified; omitting directory 'Downloads/day_5.txt/'
rtvk@rtvk-ThinkPad-E14-Gen-4:~$ cp -r Downloads/day_5.txt/ Documents/
rtvk@rtvk-ThinkPad-E14-Gen-4:~$ cd Documents/
rtvk@rtvk-ThinkPad-E14-Gen-4:~/Documents$ ls
'1 Create CA Instance 2.txt'  'Dockerfile done docker.txt'    'manager id USR urTyXeThEF6HsfJSLvSEBg.txt'   Ritvik.pdf
 day_5.txt                    'https keycloak probeplus.txt'   mongo                                        sl-devops
rtvk@rtvk-ThinkPad-E14-Gen-4:~/Documents$ 
```

### CPU / Memory
```
top
free -h
htop
```

### Disk / IO
```
df -h
du -sh /var/log
```

### Network
```
ss tulpn | grep 80
curl ifconfig.me
```

