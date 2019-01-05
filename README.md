# pvc-backup
A super simple mechanism for backing up pvcs


## Design

The core design is an operator that creates kubernetes cronjobs to backup pvcs if they have a matching backup annotation

## Limitations
This project is designed as a very simple to use and setup backup solution for pvc with backing storage that doesn't support snapshoting, for example out-of-tree provisioners.

As a side effect it is only recommended for use with applications that have some form of consitency guarentee mechanisms in place for how they use their filesystems (or at least the files you actually care about)

In my case many projects I'm using have a backup folder inside their internal database that I would like replicated to external storage on some kind of schedule.

This project is only usefull for pvcs of type ReadWriteMany. Because it mounts pvcs as ordaninary volumes it is not capable of working around limitations in kubernetes itself


## Components

Helm Chart
Rsync Container
Controller Container