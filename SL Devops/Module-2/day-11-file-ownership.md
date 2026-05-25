<img width="1917" height="140" alt="image" src="https://github.com/user-attachments/assets/6fae17ea-4f08-45c1-8f5b-6affcb20d374" />

## Task -1
## Format: -rw-r--r-- 1 owner group size date filename
## Q)What's the difference between owner and group?
- owner - the specefic user who owns the file\
eg etvk
- group - a collection of users
eg docker

## Task -2
```
touch devops-file.txt
ls -l devops-file.txt
sudo useradd -m tokyo
sudo chown tokyo devops-file.txt
sudo chown berlin devops-file.txt
ls -l
```

## Task  -3
```
touch team-notes.txt
ls -l team-notes.txt
sudo groupadd heist-team
sudo chown :heist-team team-notes.txt or sudo chgrp heist-team team-notes.txt
ls -l team-notes.txt
```

## Task -4
```
touch project-config.yaml
sudo chown professor:heist-team project-config.yaml
mkdir app-logs
sudo chown berlin:heist-team app-logs
```

## Task -5
```
chown -R professor:planners heist-project (this will change everything inside the directories)
ls -lR heist-project/
```

## Task -6
```
sudo useradd -m tokyo
sudo useradd -m berlin
sudo useradd -m nairobi

sudo groupadd vault-team
sudo groupadd tech-team

mkdir bank-heist

sudo chown tokyo:vault-team bank-heist/access-codes.txt
sudo chown -R tokyo:vault-team bank-heist
sudo chown berlin:tech-team bank-heist/blueprints.pdf
sudo chown nairobi:vault-team bank-heist/escape-plan.txt

ls -l bank-heist
