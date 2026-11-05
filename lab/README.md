# Lab files

| File | State |
|---|---|
| `Router_Redistribution_before_configuring.pkt` | Starting point: addressing and each domain's own protocol, redistribution not yet applied |
| `Router_Redistribution_final.pkt` | Finished lab with redistribution and default routes applied |

To rebuild the finished lab from the starting file, apply the commands in [`../configs/ISP-router.cfg`](../configs/ISP-router.cfg) on `ISP-router`, wait about a minute for routes to propagate, then run the checks in [`../verification/commands.md`](../verification/commands.md).
