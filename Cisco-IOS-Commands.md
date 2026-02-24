# Cisco IOS Cheat Sheet

## User Exec Mode

After logging in, the user enters the **User Exec Mode**. A prompt with the format `Hostname>` is presented.

The `?` operator can be used for obtaining help from now on. This will be useful for completing commands and fetching the list of available commands in the current context.

### Useful commands

- `enable` => Changes context to **Privileged EXEC Mode**
- `exit` => Logs out of the device
- `ping DEVICE_HOSTNAME_OR_IP_ADDRESS` => Test connectivity to a remote device
  - **Examples:** `ping google.pt` or `ping 192.168.1.1`
- `traceroute DEVICE_HOSTNAME_OR_IP_ADDRESS` => Trace route to destination address or hostname
  - **Examples:** `traceroute google.pt` or `traceroute 192.168.1.1`

## Privileged Exec Mode

After enabling the **Privileged Exec Mode**, the user gets a prompt with the following format: `Hostname#` (example: `Switch1#`). 
ℹ️ Please, notice the hash sign in the end of the prompt.

### Useful commands

- `configure terminal` => Activate **Global Configuration Mode**. A different prompt will be presented with the `(config)` part between the hostname and the hash sign: `Switch1(config)#`
- `disable` => Return to **User EXEC Mode**

## Global Configuration Mode

### Useful commands

- `end` => Return to the **Privileged EXEC Mode**. ℹ️ You can get the same result with the `CTRL+Z` shorcut.
- `exit` => Exit the **Global Configuration Mode**
- `interface` => Enter the **Interface Subconfiguration Mode**
  - **Examples:** `interface vlan 1` (for configuring the first VLAN) or `interface FastEthernet 0/1` (for configuring the port 1 on the __FastEthernet__ interface)
- `line` => Enter the **Line Subconfiguration Mode**
  - **Examples:** `line console 0` (for configuring the console connection) or `line vty 0 15` (for configuring the virtual terminal lines from 0 to 15 that are used for SSH/Telnet)

## Interface Subconfiguration Mode

### Useful commands

- `end` => Return to the **Privileged EXEC Mode**. ℹ️ You can get the same result with the `CTRL+Z` shorcut.
- `exit` => Return to the **Global Configuration Mode**

## Line Subconfiguration Mode

### Useful commands

- `end` => Return to the **Privileged EXEC Mode**. ℹ️ You can get the same result with the `CTRL+Z` shorcut.
- `exit` => Return to the **Global Configuration Mode**