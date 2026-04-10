# Common Role

Base server configuration applied to all hosts.

## What it does
- Installs common utility packages (vim, tree, htop, curl, wget)
- Sets the system timezone
- Deploys a dynamic MOTD showing hostname, IP, OS, and environment

## Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `common_packages` | `[vim, tree, htop, curl, wget]` | Packages to install |
| `common_timezone` | `UTC` | System timezone |

## Usage

```yaml
- hosts: all
  roles:
    - common
```
