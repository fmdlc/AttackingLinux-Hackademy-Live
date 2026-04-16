# Hackademy Bootstrap

This repository contains the lab setup for my EKoparty Hackademy class, **Attacking Linux**.

It automates the provisioning of a deliberately vulnerable Ubuntu environment for training and demonstration purposes.

## Included Services

- WordPress
- MariaDB
- Nginx
- PHP-FPM
- VSFTPD
- SSH password authentication enabled
- Intentionally insecure file permissions for demo scenarios

## Bundled WordPress Plugins

The setup installs and activates the following plugins from `templates/plugins`:

- `wp-autosuggest.0.24.zip`
- `wp-site-import.1.0.1.zip`

## Shell Setup

The playbook also ensures the following shell configuration is added to both `root` and `tty0` in `~/.bashrc`:

```bash
set -o vi
bind '"\C-l": clear-screen'
export PATH=$PATH:/home/tty0/.local/bin
export VISUAL=vim
export EDITOR=vim
export PAGER=vim
```

## Usage

Provision the lab:

```bash
make create
```

Remove the lab:

```bash
make remove
```
