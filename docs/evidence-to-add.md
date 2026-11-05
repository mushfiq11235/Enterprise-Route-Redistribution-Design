# Optional Extras

The repo is complete without these. Add them only if you want more evidence.

- [ ] `show ip route` on EIGRP-router-1, OSPF-router-1 and RIP_ROUTER_2
- [ ] `tracert 200.20.20.2` from `192.168.10.2`
- [ ] Save the finished lab as `lab/Router_Redistribution_final.pkt`

## Optional experiment that proves the longest-prefix-match observation

On ISP-router, under `router rip`, run `no redistribute ospf 1 metric 5`. On RIP_ROUTER_1 the `192.168.30-32.0` routes should disappear while `R* 0.0.0.0/0` stays, and `ping 192.168.30.2` should still work through the default route because the ISP router knows the OSPF networks natively. Capture `show ip route` and the ping, then restore with `redistribute ospf 1 metric 5`.

Do not screenshot anything showing browser tabs or personal information.
