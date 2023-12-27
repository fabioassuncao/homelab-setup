# HomeLab Setup

Simple script for performing initial setup on my homelab server. The tasks include package updates, workspace directory configuration, timezone setting, creation of a default user, installation of git, zip, unzip, curl, acl, docker, adding GitHub, GitLab, and Bitbucket to trusted hosts, and configuring [CapRover](https://caprover.com/) to transform the server into a user-friendly PaaS for hosting my services, complete with SSL configuration, reverse proxy, and other conveniences.

Tested on a VPS running Ubuntu Server 22.04 LTS with 4GB RAM, but can be used in similar distributions.

## Installation

To do the setup, download and run the script `install.sh` or if you prefer (proceed at your own risk), execute the instruction below.

## Usage
~~~
wget -qO- https://fabioassuncao.com/gh/homelab-setup/install.sh | bash -s -- \
--help
~~~

## Command options

You can get help by passing the `-h` option.

~~~
Script for initial configurations of Docker, Docker Swarm and CapRover.
USAGE:
    wget -qO- https://fabioassuncao.com/gh/homelab-setup/install.sh | bash -s -- [OPTIONS]

OPTIONS:
-h|--help                   Print help
-t|--timezone               Standard system timezone
--root-password             New root user password. The script forces the password update
--default-user              Alternative user (with super powers) that will be used for deploys and remote access later
--default-user-password
--workdir                   Folder where all files of this setup will be stored
--spaces                    Subfolders where applications will be allocated (eg. apps, backups)
--root-ssh-passphrase       Provides a passphrase for the ssh key
--ssh-passphrase            Provides a passphrase for the ssh key
-f|--force                  Force install/re-install

OPTIONS (Webhook):
--webhook-url               Ping URL with provisioning updates
~~~

## Important
In order for you to be able to deploy applications using git and some deployment tools such as the [deployer](https://deployer.org/), you will need to add the public key (id_rsa.pub) of the user created on your VCS server (bitbucket, gitlab, github, etc.).

## Tips

To not have to enter the password every time you need to access the remote server by SSH or have to do some deploy, type the command below. This will add your public key to the new user's ```authorized_keys``` file.

```
ssh-copy-id <USERNAME>@<SERVER IP>
```


## Contributing

1. Fork this repository!
2. Create your feature from the **develop** branch: git checkout -b feature/my-new-feature
3. Write and comment your code
4. Commit your changes: `git commit -am 'Add some feature'`
5. Push the branch: `git push origin feature/my-new-feature`
6. Make a pull request to the branch **develop**

## Credits

* [Fábio Assunção](https://github.com/fabioassuncao)
* [All Contributors](../../contributors)


## License

Licensed under the MIT License.
