# /24 CIDR Block

A **/24 CIDR block** represents a network mask where the first **24 bits** are fixed for the network portion. It translates to a standard subnet mask of **255.255.255.0**.

## Key Specifications

| Property | Value |
|-----------|--------|
| CIDR Notation | /24 |
| Subnet Mask | 255.255.255.0 |
| Total IP Addresses | 2^(32 - 24) = 2^8 = 256 |
| Usable Host Addresses | 256 - 2 = 254 |
| Reserved Addresses | 2 |

## Reserved IP Addresses

### Network ID
The first IP address in the subnet.

**Example:** `192.168.1.0`

### Broadcast Address
The last IP address in the subnet.

**Example:** `192.168.1.255`

## Example

For the subnet **192.168.1.0/24**:

| Type | Address |
|--------|---------|
| Network ID | 192.168.1.0 |
| First Usable Host | 192.168.1.1 |
| Last Usable Host | 192.168.1.254 |
| Broadcast Address | 192.168.1.255 |

## Summary

- **Subnet Mask:** `255.255.255.0`
- **Total IPs:** `256`
- **Usable Hosts:** `254`
- **Network ID:** First IP in the range
- **Broadcast Address:** Last IP in the range
- Commonly used in small to medium-sized LAN networks.
