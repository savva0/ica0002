# Restoration procedure

Infrastructure restoration involves several steps:

## Init
Hosts can be initialized with:
```sh
ansible-playbook init.yaml --ask-become-pass
```

## Wordpress
Wordpress node can be configured with:
```sh
ansible-playbook wordpress.yaml
```

## DNS
DNS nodes can be configured with:
```sh
ansible-playbook dns.yaml
```

## Backup
Backup can be configured with:
```sh
ansible-playbook backup_agent.yaml
ansible-playbook backup_server.yaml
ansible-playbook backup_agent_2nd.yaml
```

## Database
Database resotration involves several steps:
1. Fetching duplicity backup of a database
```sh
sudo -u backup HOME=/srv/backup duplicity --no-encryption restore rsync://192.168.122.133//srv/backup/db1/mariadb /srv/backup/restore
```
2. Restoring db
```sh
mariadb db < /srv/backup/restore/db.sql
```
