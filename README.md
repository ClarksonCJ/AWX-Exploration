# AWX Exploration
This repo is designed as a test and investigation for working with AWX

## Startup the Stack
Use docker compose to create the AWX stack
```
docker-compose up -d
```

There is a bug in the docker container which hosts the UI whereby the UI components are not properly symlinked.
Execute the following commands to properly symlink the ui artifacts

```
docker exec -ti awxcontainer_awx_web_1 bash
cd /var/lib/awx/public
rm -rf static
ln -s /usr/lib/python2.7/site-packages/awx/ui/static
```

## Start the Vagrant Machine
Execute the vagrant file to startup a target machine
```
vagrant up
```
This will create a local VM in virtualbox with the ip of 192.168.0.175
if this conflicts with another VM or is not part of the subnets you have assigned in your Virtual box configuration edit the vagrantfile line 18, and set the IP appropriately for your system
```
 config.vm.network "public_network", ip: "192.168.0.175"
```
NOTE: if the IP Address is changed, ensure that the host file **inventory/local/hosts** is also updated
```
[anaconda]
192.168.0.175
```
## Configure AWX to use the Project
TODO: its late, documentation to follow ;-)