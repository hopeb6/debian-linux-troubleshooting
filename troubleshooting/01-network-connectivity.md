# 01 — Network Connectivity and USB Tethering

## Environment

- OS: Debian GNU/Linux 13 (Trixie)
- Hardware: HP EliteBook 840 G6
- Network hardware: Intel Wi-Fi 6 AX200
- Temporary connection method: USB tethering

## Problem

Debian initially had no usable internet connection. The machine had network hardware, but connectivity was not working correctly.

## Symptoms

- `ip a` initially showed only the loopback interface.
- Network interfaces were down.
- `systemd-networkd` was inactive at one stage.
- DNS resolution failed.
- `ping` tests initially failed.

## Investigation

### Command

```bash
ip a
```

### Why

`ip a` shows network interfaces, their state, and assigned IP addresses. It was used to determine whether Debian could see a usable interface.

### Command

```bash
systemctl status systemd-networkd
```

### Why

This checks whether the systemd networking service is running.

### Command

```bash
sudo systemctl restart systemd-networkd
```

### Why

The service was inactive, so it was restarted to reinitialise network management.

### Command

```bash
networkctl status
```

### Why

This shows how systemd-networkd sees and manages available interfaces.

### Command

```bash
ping 8.8.8.8
```

### Why

An IP-address ping tests basic connectivity without depending on DNS.

### Command

```bash
ping google.com
```

### Why

A hostname ping tests both network connectivity and DNS resolution.

## Solution

The phone was used for USB tethering to provide the Debian host with a temporary network interface.

The USB interface appeared as an `rndis_host` device and became routable. DNS configuration was also investigated because `/etc/resolv.conf` had previously been missing.

## Result

Debian obtained working internet connectivity through USB tethering and could reach external hosts.

## Lesson Learned

Network troubleshooting should be performed in layers:

1. Is the interface present?
2. Is it up?
3. Does it have an IP address?
4. Is there a route?
5. Can it reach an IP address?
6. Does DNS work?

## Skills Demonstrated

- Linux networking
- `ip`
- `systemd-networkd`
- `networkctl`
- DNS troubleshooting
- Connectivity testing
- USB tethering
