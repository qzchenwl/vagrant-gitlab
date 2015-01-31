## Installation

1. Clone this repo
1. Install [Vagrant](http://www.vagrantup.com/) and [VirtualBox](https://www.virtualbox.org/)
1. `vagrant up`
1. `vagrant ssh`

This will create a ubuntu virtual machine with gitlab running. By default, web port forwards to `8080` and ssh port forwards to `8022`. You can change that in [Vagrantfile](Vagrantfile).

## Customization

### Hostname

Change `config.vm.hostname = "gitlab.chenwl.com"` to your own hostname. This will be hostname of your site.

Without a valid hostname, your mail sent to Gmail will be blocked.

### Port forwarding

#### SSH Port

Find line `config.vm.network "forwarded_port", guest: 22, host: 8022`, replace `8022` to any port you want ssh to connect.

Git client side need to configure ssh to connect to this port by default. Append following lines to `~/.ssh/config`.

```sh
Host gitlab.chenwl.com # replace with your hostname
  Port 8022            # replace with your ssh port
```

#### Web Port

Find line `config.vm.network "forwarding_port", guest: 80, host: 8080`, replace `8080` to any port you want your host to listen HTTP requests.
