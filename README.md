## Troubleshoots

Jenkins master cannot start due to writing file to /var/jenkins_home permission

```
chown ${USER}:${USER} ./docker/jenkins/master/home
chmod 755 ./docker/jenkins/master/home
```