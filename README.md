# Essential setup for Rasperry Pi with rsync server and Wireguard

An Ansible playbook for automating secure setup for Raspberry Pi and setting it up as rsync server with Wireguard connection.

## Description

This is my personal setup on how I set up my Rasperry Pi 4B as a rsync backup destination for 
my Synology NAS using Hyperback. The Rasperry is connected to my home network via Wireguard.

The setup is done with Ansible. To require absolute minimun to get things running, the project is also utilising devcontainers, so everything required to get things running is included.


## Getting Started

### Dependencies

* Access to Raspberry Pi via SSH using a key
    * I recommend setting the user and authorized key(s) during creation of bootable image with Raspberry Imager
* Port 51820 open (for Wireguard) on whatever network the Rasperry Pi is on
* Using VSCode with Devcontainers
    * It's absolutely possible to use this without devcontainers, but then you need to install Python and Ansible yourself.

### Installing

1. Clone this repository
2. Open the folder with VSCode
    * If things work as inteded and you get the pop-up, reopen the folder in a container

### Executing program

1. Set the variables in `.env.template` and rename the file as `.env`
2. Set the IP address of your Raspberry in `/inventory/inventory.ini`
3. If you plan to use Wireguard, edit `wg0.conf.template` as needed and rename it as `wg0.conf.template`
4. Run `source .env`
5. Run `ansible-playbook setup.yml`

## Help

If you are having many ssh-keys in your ssh-agent, you might encounter some SSH related issues/errors (such as too many authentications). If that's the case, add the details for the SSH connection to `.ssh/config` file. Here's an example:

```
Host raspberry
	HostName 192.168.1.226
	User user-name
	Port 22
	PreferredAuthentications publickey
	IdentityFile ~/.ssh/raspberry.pub

```

## Authors

Niko Kultalahti
* Website: [nikokultalahti.com](https://nikokultalahti.com)
* Mastodon: [@nikokultalahti@mas.to](@nikokultalahti@mas.to)
* Github: [github.com/nikokultalahti](https://github.com/nikokultalahti)
* LinkedIn: [in/nikokultalahti](https://linkedin.com/in/nikokultalahti)

## Acknowledgments

Sources I've looked for help and guidance.

* [mist941 / basic server configuration](https://github.com/mist941/basic-server-configuration)