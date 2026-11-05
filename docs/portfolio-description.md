# Portfolio Text

## GitHub repository description (one line)

Packet Tracer lab: RIP, EIGRP and OSPF domains joined by route redistribution on one router, plus a static default route propagated into each protocol.

## Topics (add one at a time)

```
cisco
packet-tracer
networking
ccna
route-redistribution
rip
eigrp
ospf
static-routing
default-route
```

## Short summary (resume / LinkedIn project entry)

Built a Packet Tracer lab with three LAN domains running RIP, EIGRP and OSPF, connected through a single redistribution router. Configured redistribution in all six directions with a seed metric suited to each protocol, and propagated a static default route into every domain. Checked results with routing tables (`R`, `D EX`, `O E2`, `R*`) and end-to-end pings, and documented the setup in a README.

## Resume bullets (pick two)

- Configured mutual route redistribution between RIP, EIGRP and OSPF on one router in Cisco Packet Tracer, using protocol-specific seed metrics, so LANs in different routing domains could reach each other.
- Propagated a static default route into RIP, OSPF and EIGRP (`default-information originate` and `redistribute static`) and explained why more specific redistributed routes win over it by longest-prefix match.
- Checked redistribution through routing-table analysis (`O E2`, `D EX`, `R*`) and ping tests, and documented troubleshooting steps and limitations.

## Interview talking points

- Why protocols do not share routes by themselves, and what an ASBR is.
- Why each protocol needs a different metric (hop count, composite, OSPF cost).
- Why a single redistribution point avoids loops, and what changes with two.
- Why the default route needs a different command in each protocol.
- Longest-prefix match: why specific routes beat `0.0.0.0/0`.
- Honest limitations: simulator only, everything redistributed with no filtering, two items still to capture.
