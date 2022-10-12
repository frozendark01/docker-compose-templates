# docker-compose-templates
A set of collections of docker-compose templates!
##
useful tool for conversion from docker run to docker-compose https://www.composerize.com/
##
Configuring remote access with systemd unit file
<pre>Use the command `sudo systemctl edit docker.service` to open an override file for docker.service in a text editor.
```
[Service]
ExecStart=
ExecStart=/usr/bin/dockerd -H fd:// -H tcp://0.0.0.0:2375
```
</pre>
`sudo systemctl restart docker.service`