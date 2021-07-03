# xrdp_server

Install XRDP server and prepare sharing a Linux desktop environment over RDP.

## Requirements

* Ubuntu 20.04, Focal

## Role Variables

* `xrdp_server_desktop_environment` --- Which desktop environment to install, default `gnome`.
    * `gnome` == The vanilla Gnome desktop environment
* `xrdp_server_enable_sound` --- Enable sound redirect, default `true`.
* `xrdp_server_disconnected_timeout_seconds` --- If `>0` then disconnected sessions will be killed, default `0`.
* `xrdp_server_idle_timeout_seconds` --- If `>0` then disconnects session after idle time, default `0`.
* `xrdp_server_loglevel` --- Set loglevel to core, error, warning, info or debug, default `warning`.
* `xrdp_server_max_sessions` --- Maximum number of connected clients, default `10`.

Security related.

* `xrdp_server_allow_root_login` --- Allow graphical login for root, default `false`.
* `xrdp_server_group_check` --- Check if user in `tsusers` or admin in `tsadmins`, default `false`.
* `xrdp_server_restrict_outbound_clipboard` --- Allow graphical login for root, default `false`.

## Dependencies

None.

## Example Playbook

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

## License

GPL-2.0

## Author Informatiom

Arnulf Heimsbakk
