# xrdp_server

Sets up desktop sharing with RDP. Install [neutrinolabs](https://github.com/neutrinolabs) XRDP server and a desktop environment.

## Version

* `main` --- latest development release, not for production

## Requirements

* Fedora 34
* Ubuntu 20.04, Focal
* Ubuntu 21.04, Hirsute
* Ubuntu 21.10, Impish

## Role Variables

* `xrdp_server_desktop_environment` --- Which desktop environment to install, default `gnome`.
    * `gnome` --- The vanilla Gnome desktop environment.
<!---
* `xrdp_server_xrdp_source_build` --- Build xrdp from source, default `false`.
* `xrdp_server_xrdp_source_version` --- Version of source to use, default `v0.9.16`.
* `xrdp_server_xrdp_xorgxrdp_source_version` --- Version of source to use, default `v0.2.16`.
-->
* `xrdp_server_disconnected_timeout_seconds` --- If `>0` then disconnected sessions will be killed after seconds, default `0`.
* `xrdp_server_idle_timeout_seconds` --- If `>0` then disconnects session after idle time, default `0`.
* `xrdp_server_loglevel` --- Set log level to core, error, warning, info or debug, default `warning`.
* `xrdp_server_max_sessions` --- Maximum number of connected clients, default `10`.
* `xrdp_server_sound_driver_version` --- Version of neutrinolabs driver to use, default `v0.5`
* `xrdp_server_sound_enable` --- Enable sound redirect - Ubuntu only, default `false`.
* `xrdp_server_tigervnc_enable` --- Use tigervnc instead of `xorgxrdp`, default `false`.

Security related.

* `xrdp_server_allow_root_login` --- Allow graphical login for root, default `false`.
* `xrdp_server_group_check` --- Check if users are in `tsusers` or admins are in `tsadmins`, default `false`.
* `xrdp_server_restrict_outbound_clipboard` --- Disable outbound clipboard, default `false`.

## Dependencies

None.

## Example Playbook

    - name: install XRDP with sound redirect on Ubuntu
      hosts: all
      become: true
      roles:
        - role: xrdp_server
          xrdp_server_desktop_environment: gnome
          xrdp_server_disconnected_timeout_seconds: 60
          xrdp_server_idle_timeout_seconds: 86400
          xrdp_server_loglevel: error
          xrdp_server_max_sessions: 25
          xrdp_server_sound_enable: true

## Testing

### Test environment for all OSes

```bash
cd tests
vagrant up
```

### Rerun role

Run role on all OSes again.

```bash
vagrant provision
```

### Debug interactively

This uses cluster ssh to work with all vagrant boxes at the same time.

```bash
vagrant ssh-config > ~/.ssh/config
cat ~/.ssh/config | grep ^Host | cut -d\  -f2 | xargs cssh
```

## License

GPL-2.0

## Author Informatiom

Arnulf Heimsbakk

<!---
vim: set spell spelllang=en:
-->
