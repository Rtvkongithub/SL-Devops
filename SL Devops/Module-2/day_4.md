# Day 04 – Linux Practice: Processes and Services

## Process Checks

### 1. Check Running Processes

Command:
```
ps aux | head -h
pgrep
```

### 2. service commands
```
systemctl docker status
systemctl start nginx
```

### 3. log commands
```
docker logs ....
tail -n /var/log/syslog
```

### 4. work flow
#### SSH service not responding
```
systemctl status ssh
journalctl -u ssh
systemctl restart ssh
```
