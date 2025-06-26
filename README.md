# et101-repo

During my on-call shift, one limit order triggered a PV5 error. Initially, it appeared to be a market impact breach, as the system attempted to slice a market order.

After further investigation — thanks to Isaac and the team — we found the root cause was in the spread calculation logic. The analytics used an outdated turnover time (~30 minutes) seeded by the quant file, which was no longer reflective of the actual trading behavior after a stock split. As a result, the computed spread became stale and overly wide (around $49), leading to a negative calculated price after pegging, which got floored to zero. This behavior caused the system to interpret it as an attempt to send a market order, triggering the PV5 rejection.

The team also noted that the spread calculation fell back to stale bid/ask values when turnover was high, further exacerbating the issue. A possible improvement discussed was to add bounding logic or a fallback to real-time market data when the spread appears clearly incorrect.

