# Verification Commands

Copy-paste lists for the Packet Tracer CLI. Run in privileged EXEC mode (`enable` first if prompted).

Some variants differ between Packet Tracer and real IOS. If a command is rejected, try a shorter form.

## Any router

```
show ip interface brief
show ip protocols
show ip route
show running-config
```

## ISP-router (redistribution point)

```
show ip route rip
show ip route eigrp
show ip route ospf
show ip route static
show running-config | section router
show ip ospf database external
show ip eigrp topology
show ip protocols
```

## Domain routers (what the redistributed routes look like)

```
! RIP_ROUTER_1 / RIP_ROUTER_2   -> expect R routes and R* 0.0.0.0/0
show ip route rip

! EIGRP_ROUTER_1 / EIGRP_ROUTER_2 -> expect D EX routes and D*EX 0.0.0.0/0
show ip route eigrp
show ip eigrp topology

! OSPF_ROUTER_1 / OSPF_ROUTER_2 -> expect O E2 routes and O*E2 0.0.0.0/0
show ip route ospf
```

## IGW_BTCL (internet gateway)

```
show ip route
ping 100.10.10.2
```

## End-to-end tests from PCs (Command Prompt tab)

```
ping 192.168.30.2        (from 192.168.10.2, RIP LAN -> OSPF LAN)
ping 192.168.20.2        (from 192.168.10.2, RIP LAN -> EIGRP LAN)
ping 192.168.10.2        (from 192.168.20.2, EIGRP LAN -> RIP LAN)
ping 192.168.30.2        (from 192.168.20.2, EIGRP LAN -> OSPF LAN)
ping 192.168.10.2        (from 192.168.30.2, OSPF LAN -> RIP LAN)
ping 192.168.20.2        (from 192.168.30.2, OSPF LAN -> EIGRP LAN)
ping 200.20.20.2         (from each LAN, tests the propagated default route)
tracert 200.20.20.2      (from each LAN)
```

The first pings after a change often time out while routes propagate. Repeat the ping.

## What to look for

| Check | Expected |
|---|---|
| `show ip route` on RIP_ROUTER_1 | `R` routes for 192.168.20-22.0 and 30-32.0, plus `R* 0.0.0.0/0` |
| `show ip route` on OSPF_ROUTER_1 | `O E2 [110/20]` for the RIP and EIGRP networks, plus `O*E2 0.0.0.0/0` |
| `show ip route` on EIGRP routers | `D EX [170/...]` for the RIP and OSPF networks, plus `D*EX 0.0.0.0/0` |
| `show ip route` on ISP-router | `S* 0.0.0.0/0 [1/0] via 100.10.10.1`, plus native `R`, `D`, `O` routes |
| Ping to a redistributed LAN | Replies after convergence; TTL 123 across five routers |
| Ping to 200.20.20.2 | Succeeds via the default route (return path needs the default on IGW_BTCL) |

## Captured outputs in this repo

See [`captured-outputs/`](captured-outputs/).
