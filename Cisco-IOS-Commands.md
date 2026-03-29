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

<br/>
<br/>
<br/>
<br/>

## Privileged Exec Mode

After enabling the **Privileged Exec Mode**, the user gets a prompt with the following format: `Hostname#` (example: `Switch1#`). 
ℹ️ Please, notice the hash sign in the end of the prompt.

### Useful commands

- `clear aaa local user lockout username <username>` => This clears the account lockout tied to the local `<username>` account
- `copy running-config startup-config` => Copies the current and running configuration from the **RAM** to the non-volatile **NVAM** storage. 📝 You can use the shorthand `copy run start` for the same effect.
- `copy startup-config running-config ` => Copies the configuration stored in **NVRAM** and applies it to the running configuration on the **RAM**.
- `configure terminal` => Activate **Global Configuration Mode**. A different prompt will be presented with the `(config)` part between the hostname and the hash sign: `Switch1(config)#`.
- `dir` => List the files of a file system.
   - **Examples:** `dir flash:` or `dir nvram:` for showing the location of the __Flash__ memory or __NVRAM__, respectively.
- `disable` => Return to **User EXEC Mode**.
- `erase startup-config` => Removes the start up configuration from **NVRAM**. ❗This needs to be used with **CAUTION**! Usually, you reload the device with `reload` command after issuing this instruction.
- `reload` => Stops the system and perform a cold restart.
- `show ip interface brief` => Show IPV4 information about the device interfaces.
- `show ipv6 interface brief` => Show IPV6 information about the device interfaces.
- `show running-config` => Show current operating configuration, including line config. and access config.

<br/>
<br/>
<br/>
<br/>

## Global Configuration Mode

### Useful commands

- `banner motd MESSAGE` => Sets **Message Of The Day** banner. ⚠️ **Warning:** the message needs to be delimited by two special characters like `"MESSAGE"` or `#Message#`.
  - **Example:** `banner motd "Authorized access only!"` (will set the MOTD to `Authorized access only!`)
- `default interface <INTERFACE_ID>` => Erase all custom configuration from the `<INTERFACE_ID>` and return it to its default state.
  - **Example:** `default interface g0/1` (will erase all configuration from GigabitEthernet 0/1)
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
- `ip default-gateway <DEFAULT_GATEWAY_IP>` => Configures the default gateway for the switch/router
- `ip route <DESTINATION_NETWORK> <SUBNET_MASK> <NEXT_HOP_IP>` => Adds a route to the router
- `line` => Enter the **Line Subconfiguration Mode**.
  - **Examples:** `line console 0` (for configuring the console connection) or `line vty 0 15` (for configuring the virtual terminal lines from 0 to 15 that are used for SSH/Telnet)
- `no ip domain-lookup` => Prevents IOS from attempting to resolve mistyped commands to domain names
- `security password min-length <MIN_LENGTH>` => Sets the minimum password length to `<MIN_LENGTH>` for new users
- `service password-encrypt` => Encrypt all plaintext passwords.

<br/>
<br/>
<br/>
<br/>

## Interface Subconfiguration Mode

### Useful commands

- `duplex <DUPLEX_MODE>` => Sets the duplex mode. **Possible values:** `half`, `full` and `auto` 
- `end` => Return to the **Privileged EXEC Mode**. ℹ️ Tip: you can get the same result with the `CTRL+Z` shorcut.
- `exit` => Return to the **Global Configuration Mode**.
- `ip address ip-address subnet-mask` => Assign an **IPv4** address and a subnet mask to a device on an interface.
  - **Example:** `ip address 192.168.1.100 255.255.255.0` (for setting the `192.168.1.100` as the device's IPv4 address and setting `255.255.255.0` as the submask).
- `ipv6 address <ip-address>/<prefix-length>` => Assign an **IPv6** address with the respective prefix to a device on an interface.
  - **Example:** `ipv6 address 2001:db8:acad:1::1/64` (for setting the `2001:db8:acad:1::1` as the device's IPv6 address with `/64` prefix in slash notation).
- `ipv6 address <ipv6-address> link-local` => Assign an **IPv6** link-local address (LLA) to a device on an interface.
  - **Example:** `ipv6 address fe80::1:1 link-local` (for setting the `fe80:0000:0000:0000:0000:0000:0001:0001` as the device's IPv6 LLA address).
- `ip default-gateway ip-address` => Assign the default gateway **IP** address in a device. This can be the router which the switch connects to.
- `no shutdown` => Enable the virtual interface that was configured with the **IP** address.
- `switchport mode <ACCESS>` => Changes the switch port mode. **Possible values:** `access`, `trunk` or `dynamic`

<br/>
<br/>
<br/>
<br/>

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