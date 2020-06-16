Title: Gitea in a FreeBSD jail
Date: 2019-05-27
Category: Git
Tags: git, FreeBSD, jails
Slug: gitea-in-a-jail
Authors: L.J. Hanson
Summary: Gitea in a jail

I run a server at home, primarily for file shares but backups as well.  One thing that I felt might be easier is running git on the server to better integrate into my workflow as well as working better than git on a shared drive.

To install gitea on my FreeBSD server I took the following steps:

* Create a new jail
* Install gitea and enable it:

```bash
root@git:~ #pkg install gitea bash
root@git:~ #sysrc gitea_enable=YES
```

Bash was needed as it wasn't a requirement of gitea but was needed later during the install, this may be fixed when you do this next time.

* Configure gitea

You can either do this by editing the app.ini directly or deleting the app.ini file and temporarily opening up permissions for gitea to create/edit the file itself. If you chose to have the app do by itself, start the app up as follows:

```bash
root@git:~ #service gitea start
```

Gitea should now be accessible at <http://localhost:3000>.  If the box is remote you may need to combine both these approaches to configure.
