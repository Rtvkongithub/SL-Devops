<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6e140d15-48ee-41e4-a499-f279df3c6da9" />

## verifying
```
http://<EC2-pub ip>
```
## Access log and error
```
sudo tail -f /var/log/nginx/access.log
```
```
sudo tail -f /var/log/nginx/error.log
```

## copying the file
```
sudo cp /var/log/nginx/access.log ~/access.log
```
or
```
sudo journalctl -u nginx > ~/access1.log
```

