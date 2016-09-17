This repo contains my various development setups as Docker files.

# Installing

Install docker (https://www.docker.com/products/docker).
Install XQuarts (https://www.xquartz.org/) for copy/paste between systems.
Note: ensure syncing is enabled under XQuartz -> Preferences -> Pasteboard

clone repo, cd into repo, and run
` make `

when you are done run `make stop`

Put this in ``` ~/.ssh/config ``` (making sure to replace the username which whatever your $USER is):

```
Host devbox
  HostName localhost
  Port 22
  User <insert your username here>
  ForwardAgent true
  # required for copy / paste between systems
  ForwardX11 yes

  # prevent remote host identification warnings
  StrictHostKeyChecking no
  UserKnownHostsFile=/dev/null
```

then run:

```
ssh devbox
```

Note:

Connecting to devbox requires that you have your public keys in the authorized_keys file here:

```
/home/$USER/.ssh/authorized_keys
```

A useful way to do this is to install github-auth locally and add the keys to your enviornment prior to running ``` make ```

```
# ssh
# https://github.com/chrishunt/github-auth
gem install github-auth --no-rdoc --no-ri
gh-auth add --users=$USER
```

# Boxes

The following devbox variants currently exist:

* [base](./base)
* [elixir-postgres](./elixir-postgres)

# Known Issues

Running Vim inside the first TMUX pane created will not allow seamless navigation between splits (workaround is to just kill the first split).
