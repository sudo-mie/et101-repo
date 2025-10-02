

First order, is a VWAP with force complete in close auction enabled, but didn't complete.
This is primarily driven by the EHV calculation. For VWAP, it won't trade up to 4PM, its schedule ends before 4 with the offset. However, the EHV used for forecasting continuous qty during force close calculation is always 4PM. So it is overestimating the continuous volume, and the order ended up not completing with the max rate constraints. 

The attached jira will fix the EHV calculation for force close. 

