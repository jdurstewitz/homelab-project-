# SSH Timeout Troubleshooting: DHCP IP Change After Extended Downtime

## The Problem
After my home Ubuntu Server (running CasaOS) was powered off for several months, I powered it back on and attempted to SSH into it using the previously known IP address.

**Symptoms:**
- `ssh` connection attempt timed out
- `ping` to the known IP returned "Destination host unreachable"

"Destination host unreachable" specifically indicates the network couldn't find a path to that address at all pointing me toward an IP/addressing issue rather than a blocked service.

## Diagnostic Process

**1. Confirmed physical boot success**
Preformed a hard reset on laptop, waited for it to post and then logged into the server when prompted.

**2. Checked the server's actual current IP**
```bash
ip a
```
This revealed the server's current IP address did not match the IP I had been trying to connect to.

**3. Root cause identified**
After months offline, the router's DHCP lease for the server had expired, and on reboot the server was assigned a new IP address by DHCP.

**4. Verified the fix**
Attempted SSH again using the new IP address  connection succeeded immediately.

## Resolution
Connected via SSH using the correct, current IP address obtained from `ip a`.

## Prevention Going Forward
To prevent this from recurring, I'm configuring a static IP directly on the server (via Netplan) since my ISP-provided router has limited configuration access and doesn't support setting a DHCP reservation. This assigns the server a fixed IP address outside the router's DHCP range, ensuring it stays consistent across reboots and extended downtime.
*UPDATE* Im still facing issues with editing settings in my ISP provided equipment, I will be sourcing my own hardward to give me more freedom to make DHCP changes

## Skills Demonstrated
- Systematic network troubleshooting methodology (physical access → local diagnostics → root cause → verification)
- Interpreting `ping` error messages (`Destination host unreachable` vs. connection timeout/refused)
- Using `ip a` to inspect network interface configuration
- Understanding DHCP lease behavior and its practical failure modes
- SSH connectivity troubleshooting
