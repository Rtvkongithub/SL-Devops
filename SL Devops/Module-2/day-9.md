## Task - 1
```
sudo useradd -m tokyo
sudo useradd -m berlin
sudo useradd -m professor
```
```
cat /etc/passwd
or
cd /
ls /home
```
<img width="1920" height="396" alt="image" src="https://github.com/user-attachments/assets/8d4a9335-ab20-498d-81aa-dcbd7af48428" />

## Task -2
```
sudo groupadd developers
sudo groupadd admins
```
checking -> /etc/group

## Task -3
```
sudo usermod -aG developers tokyo
sudo usermod -aG developers,admins berlin
sudo usermod -aG admin 
```
to check -> groups tokyo...groups berlin...groups professor

## Task -4
```
sudo mkdir /opt/dev-project
sudo chown :developers /opt/dev-project
sudo chmod 755 /opt/dev-project
sudo -su tokyo
exit
sudo su - berlin
touch /opt/dev-project/hai.txt
```

## Task -5
```
sudo useradd -m nairobi
sudo groupadd project-team
sudo usermod -aG project-team nairobi
sudo mkdir /opt/team-workspace
sudo chown :project-team /opt/team-workspace
sudo chmod 775 /opt/team-workspace
sudo su - nairobi
touch /opt/team-workspace/abc.txt
```
