# Windbg commands to know

* `r` - show all regiters
* `d` - dump (repeats last dump command i.e. db, dt, d...
  * `db` - dump bytes
* `poi(<address>)` -	Follow reference for the given pointer (handle) address - handles endianess at least little endian

Dump data at pointer address:
* d poi(rdx+0x8) - dumps the data at the pointer located in rdx+0x8

# JavaScript stuff

link: https://doar-e.github.io/blog/2017/12/01/debugger-data-model/


# Vmware ip address resolution issues

## OS: Ubuntu 18.04

When cloning a vm and running it on the same network, it is not enough to just change the mac and reboot. It appears Ubuntu 18.04 needs dhcp to be changed to using `mac` as an identifier. To do this, do the following:

```bash
sudo vi /etc/netplan/xxx.cfg
```

then add 

```bash
dhcp-identifier: mac
```

to each of the interfaces you would like the ip to be different

Resource:
- https://communities.vmware.com/thread/600978

# TMUX fu

```bash
:setw synchronize-panes           
```

# Install 32-bit bins on Ubuntu

```bash
dpkg --add-architecture i386
apt-get update
apt-get install libc6:i386 libstdc++6:i386
```
# Vscode setup 

Add terminal focus switching by adding the following to keybindings.json

```json
{
  "key": "shift+cmd+]",
  "command": "workbench.action.terminal.focusNext",
  "when": "terminalFocus"
}
```

Reference:
- https://stackoverflow.com/questions/48440673/how-to-switch-between-terminals-in-visual-studio-code#:~:text=Once%20the%20cursor%20is%20in,or%20ctrl%2Bx%20right%20).k

# IPython Autoreload 

Must have for interactive dev

Create a profile:

```bash
ipython profile create
```

Add reload to profile located here `~/.ipython/profile_default/ipython_config.py`:

```bash
c.InteractiveShellApp.extensions = ['autoreload']
c.InteractiveShellApp.exec_lines = ['%autoreload 2']
c.InteractiveShellApp.exec_lines.append('print("Warning: disable autoreload in ipython_config.py to improve performance.")')
```

Reference:
- https://www.keybits.net/posts/configure-autoreload-for-ipython/
