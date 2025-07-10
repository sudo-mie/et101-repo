# et101-repo


Hi Everyone. Thanks for joining.

So today I’ll give a quick summary of the rota issues we encountered in the last sprint. 

Let’s start with the first issue:

#### 1
There was a order that didn’t execute for some period of time. It was amended at 11:43 to increase the participation rate, but we didn’t trade again until 11:51. 


After investigation, we found that during the time period, we were keep posting. However the market kept moving away from our posted slices, so no execution.
Also, we were ahead of schedule, and no deficit qty to trigger sweep. So we were trading passively, only posting during that time.


#### 2
Second issue is a hydra order that didn’t complete.


When we allocated the close auction quantity at 15:59, there was no predicted residual quantity.


And during the last minute, we don’t have enough incentive to trigger the sweep. Hydra has triggered force completion, and it reduced the width of the participation rate band to force the algo use a higher rate. However, using a higher participation rate won’t guarantee to sweep, especially given the time interval is only 1 minute.

#### 3
Third order is a VWAP that trades faster than expected.
For this order, we observed a significant increase in market volume for this symbol. The modelVol is 10 to 15 times of historical Vol.


So, we believe the root cause is the two unexpected large volume spikes had the effect of causing the algo to frontload its scheduling.


We’ve been working on a new scheduling model for algo and rolling it out soon. We think the new approach can better handle volumn spikes like this.

#### 4 
Fourth order is a BSOR order. It was originally 1 share, and was amended to 15K, but only ever sliced 1 share.


For this order, we found an issue with the code. The childOrder price is set as 0 since it is a market order, so effectivePrice is always passive.
According to this code, instead of amending the child quantity for the auction, we early return and do nothing.


It is an edge case that only applies to BSOR dquote direct orders. There is a jira attached, will fix the issue and patch the prod version. Besides, another next step is we can add some monitoring to make sure bsor orders are fully sliced out to catch edge case like this one.


#### 5
The fifth order has a minqty of 10 thousands on order, but still traded in small lots.


This is because the order triggered sweeping from leaves cleanup logic. Leaves cleanup mode is set to Sweep, which is the default, and the cleanup logic would trigger when the leaves become less than the CleanUpQty. For this order LeavesCleanupQty is set to 10,000, triggering the sweeping immediately.
For the next step, we’ll look into how to improve this logic. Attached the email from the product team.

#### 6
The next order, it didn’t complete, there are 120k shares not trade. 
The symbol was halted at 3:49:44. The Scheduler has reserved about 75 thousands shares for close auction, but it never got sliced out. 


This is because, when a symbol is halted, the order placement enters a special logic that only handles continuous trading logic. 
So, when the halted period overlaps with the close auction order submission window, the slice will be blocked and cannot slice out. 
For the next step, we will fix the logic and the jira is attached here.

#### 7
The last order is a Hydra order that didn’t complete even with force complete triggered. As we mentioned before, when the Hydra force complete triggered, it reduced the width of the participation rate band, and we have observed the order has target pov rate increased to 90% at 3:58, based on volume forecast at that time. However, in reality there wasn’t enough additional eligible volume in the last 2 minutes to fully complete the order.
So, this is expected behavior due to the overestimated volume forecast. No next step at this time.



That’s all the issues for this sprint. Any questions?
Thanks for joining, have a nice day.




