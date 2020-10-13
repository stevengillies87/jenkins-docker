# Clyde Space Jenkins

## Deployment
Create .env file based on example.env
`./deploy.sh`


## Host Dockerd configuration
Replace ExecStart line in /lib/systemd/system/docker.service with
"ExecStart=/usr/bin/dockerd -H tcp://0.0.0.0:4243 -H unix:///var/run/docker.sock"

```
sudo systemctl daemon-reload
sudo service docker restart
```


## Jenkins configuration
Install Docker plugin (Jenkins Dashboard –> Manage Jenkins –> Manage Plugins)
Jenkins Dashboard –> Manage Jenkins –> Configure system –> Configure Cloud
Add Docker cloud, URI is tcp://<HOST_IP>:4243
Test connection and you should see Docker version number of host daemon