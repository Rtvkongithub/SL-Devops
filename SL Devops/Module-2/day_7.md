## Hierachy
- / - top dir
- /home - user home dir(abc ,rtvk)
- /root - root users home dir

- /etc - config files
- /user/bin - user command bin
- /opt - optional / third party

```
du -sh /var/log/* 2>/dev/null | sort -h | tail -5
```
+ disk usage
+ summary in human readable
+ all the files and folder inside val log
+ stderr redirects dev/null(blackhole(everything dissapears))

## Part -2
- systemctl status nginx
- systemctl list-units --type=service
- systemctl is-enabled nginx

## Own way
```
systemctl status myapp
```
- allows to see if the system is active, failed or stopped
```
journalctl -u myapp -n 20
```
- to see the last 20 lines
```
systemctl is-enabled myapp
```

