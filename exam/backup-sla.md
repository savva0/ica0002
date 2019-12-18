# Backup SLA
This document describes backup service SLA.

## Coverage
This backup solution covers only MariaDB database on __db1__ as the state of the rest of the service can be restored with Ansible. Database is dumped to /srv/backup with mysqldump and then backedup with Duplicity.

## Frequency
Full backup is performed every Saturday at 23.00 and incremented backup is done every day at 23.00.

## Retention
Full backups are kept for a one year and incremental chains for six months. Full incremental chain is deleted only when most recent increment is six months old. Deletion is done manually.

## Usability and availability
Make sure that backup works by restoring infra to a state on a test environment.

## Security
Backup files are transfered over secure authenticated encrypted channel (SSH). Files are not encrypted.

## Storage
MariaDB dumps are stored on two different servers, __db1__ and __backup_server1__.

## Documentation
Documentation consists of main [README.md](README.md), this file (backup-sla.md) and Ansible Playbook files.
