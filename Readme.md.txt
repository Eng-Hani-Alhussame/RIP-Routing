# RIP Routing Configuration Lab (Concise)

## Topology (Chain)
```

LAN2 (192.168.2.0/24) → Router0 → (3.0/24) → Router2 → (5.0/24) → Router3 → (6.0/24) → Router4 → (7.0/24) → Router1 → LAN1 (192.168.1.0/24)

```

## IP Addressing
| Router  | Interface        | IP Address       |
|---------|------------------|------------------|
| Router0 | Fa0/0            | 192.168.2.1/24  ; |
| Router0 | Fa0/1            | 192.168.3.1/24  ; |
| Router2 | Fa0/0            | 192.168.3.2/24  ; |
| Router2 | Fa0/1            | 192.168.5.1/24  ; |
| Router3 | Fa0/0            | 192.168.5.2/24  ; |
| Router3 | Fa0/1            | 192.168.6.1/24  ; |
| Router4 | Fa0/0            | 192.168.6.2/24  ; |
| Router4 | Fa0/1            | 192.168.7.1/24  ; |
| Router1 | Fa0/0            | 192.168.7.2/24  ; |
| Router1 | Fa0/1            | 192.168.1.1/24  ; |

## RIP Networks
All directly connected subnets are advertised with RIPv2:
- 192.168.2.0
- 192.168.3.0
- 192.168.5.0
- 192.168.6.0
- 192.168.7.0
- 192.168.1.0

## Configurations

### Router0
```

enable
configure terminal
hostname Router0
interface FastEthernet0/0
ip address 192.168.2.3 255.255.255.0
no shutdown
interface FastEthernet0/1
ip address 192.168.3.1 255.255.255.0
no shutdown
router rip
version 2
no auto-summary
network 192.168.2.0
network 192.168.3.0

```

### Router2
```

enable
configure terminal
hostname Router2
interface FastEthernet0/0
ip address 192.168.3.2 255.255.255.0
no shutdown
interface FastEthernet0/1
ip address 192.168.5.1 255.255.255.0
no shutdown
router rip
version 2
no auto-summary
network 192.168.3.0
network 192.168.5.0

```

### Router3
```

enable
configure terminal
hostname Router3
interface FastEthernet0/0
ip address 192.168.5.2 255.255.255.0
no shutdown
interface FastEthernet0/1
ip address 192.168.6.1 255.255.255.0
no shutdown
router rip
version 2
no auto-summary
network 192.168.5.0
network 192.168.6.0

```

### Router4
```

enable
configure terminal
hostname Router4
interface FastEthernet0/0
ip address 192.168.6.2 255.255.255.0
no shutdown
interface FastEthernet0/1
ip address 192.168.7.1 255.255.255.0
no shutdown
router rip
version 2
no auto-summary
network 192.168.6.0
network 192.168.7.0

```

### Router1
```

enable
configure terminal
hostname Router1
interface FastEthernet0/0
ip address 192.168.7.2 255.255.255.0
no shutdown
interface FastEthernet0/1
ip address 192.168.1.3 255.255.255.0
no shutdown
router rip
version 2
no auto-summary
network 192.168.7.0
network 192.168.1.0

```
-Eng-Hani Alhussame