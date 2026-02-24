# Cisco IOS Cheat Sheet

## User Exec Mode

After logging in, the user enters the **User Exec Mode**. A prompt with the format `Hostname>` is presented.

The `?` operator can be used for obtaining help from now on. This will be useful for completing commands and fetching the list of available commands in the current context.

### Useful commands

- `enable` => Changes context to **Privileged EXEC Mode**.
- `exit` => Logs out of the device.
- `ping DEVICE_HOSTNAME_OR_IP_ADDRESS` => Test connectivity to a remote device.
  - **Examples:** `ping google.pt` or `ping 192.168.1.1`
- `traceroute DEVICE_HOSTNAME_OR_IP_ADDRESS` => Trace route to destination address or hostname.
  - **Examples:** `traceroute google.pt` or `traceroute 192.168.1.1`

## Privileged Exec Mode

After enabling the **Privileged Exec Mode**, the user gets a prompt with the following format: `Hostname#` (example: `Switch1#`). 
ℹ️ Please, notice the hash sign in the end of the prompt.

### Useful commands

- `copy running-config startup-config` => Copies the current and running configuration from the **RAM** to the non-volatile **NVAM** storage. 📝 You can use the shorthand `copy run start` for the same effect.
- `copy startup-config running-config ` => Copies the configuration stored in **NVRAM** and applies it to the running configuration on the **RAM**.
- `configure terminal` => Activate **Global Configuration Mode**. A different prompt will be presented with the `(config)` part between the hostname and the hash sign: `Switch1(config)#`.
- `dir` => List the files of a file system.
   - **Examples:** `dir flash:` or `dir nvram:` for showing the location of the __Flash__ memory or __NVRAM__, respectively.
- `disable` => Return to **User EXEC Mode**.
- `erase startup-config` => Removes the start up configuration from **NVRAM**. ❗This needs to be used with **CAUTION**! Usually, you reload the device with `reload` command after issuing this instruction.
- `reload` => Stops the system and perform a cold restart.
- `show ip interface brief` => Show information about the device interfaces.
- `show running-config` => Show current operating configuration, including line config. and access config.


## Global Configuration Mode

### Useful commands

- `banner motd MESSAGE` => Sets **Message Of The Day** banner. ⚠️ **Warning:** the message needs to be delimited by two special characters like `"MESSAGE"` or `#Message#`.
  - **Example:** `banner motd "Authorized access only!"` (will set the privileged level password to `cisco`)
- `enable password` => Set the privileged level password.
  - **Example:** `enable password cisco` (will set the privileged level password to `cisco`)
- `enable secret` => Set the privileged level secret. ⚠️ **Warning:** setting the secret will override the privileged level password.
  - **Example:** `enable secret class` (will set the privileged level secret to `class`)
- `end` => Return to the **Privileged EXEC Mode**. ℹ️ Tip: you can get the same result with the `CTRL+Z` shorcut.
- `exit` => Exit the **Global Configuration Mode**.
- `hostname` => Change the hostname of the current device.
  - **Example:** `hostname SwitchOnArea1` (will change the prompt to `SwitchOnArea1#`)
- `interface` => Enter the **Interface Subconfiguration Mode**.
  - **Examples:** `interface vlan 1` (for configuring the first VLAN) or `interface FastEthernet 0/1` (for configuring the port 1 on the __FastEthernet__ interface)
- `line` => Enter the **Line Subconfiguration Mode**.
  - **Examples:** `line console 0` (for configuring the console connection) or `line vty 0 15` (for configuring the virtual terminal lines from 0 to 15 that are used for SSH/Telnet)
- `service password-encrypt` => Encrypt all plaintext passwords.

## Interface Subconfiguration Mode

### Useful commands

- `end` => Return to the **Privileged EXEC Mode**. ℹ️ Tip: you can get the same result with the `CTRL+Z` shorcut.
- `exit` => Return to the **Global Configuration Mode**.
- `ip address ip-address subnet-mask` => Assign an **IP** address and a subnet mask to a device on an interface.
  - **Example:** `ip address 192.168.1.100 255.255.255.0` (for setting the `192.168.1.100` as the device's IP address and setting `255.255.255.0` as the submask.
- `ip default-gateway ip-address` => Assign the default gateway **IP** address in a device. This can be the router which the switch connects to.
- `no shutdown` => Enable the virtual interface that was configured with the **IP** address.

## Line Subconfiguration Mode

### Useful commands

- `end` => Return to the **Privileged EXEC Mode**. ℹ️ Tip: you can get the same result with the `CTRL+Z` shorcut.
- `exit` => Return to the **Global Configuration Mode**
- `login` => Enable password checking.
- `password` => Change the line password. ⚠️ Warning: you need to execute the `login` command after setting the password.
  - **Example:** `password cisco` (changes the current line password to cisco)

## Most Useful Shortcuts

- `CTRL+C` => Abort certain comands
- `CTRL+D` => Delete the character on the right of the cursor
- `CTRL+SHIFT+6` => Abort current ping/traceroute/DNS lookup/etc
- `Up Arrow` => Move to the previous command on the history buffer
- `Down Arrow` => Move to the next command on the history buffer
- `Tab` => Complete the current command that is being written on the prompt