# et101-repo



Subject: Follow-up on H-1B Extension Filing – Still Showing "Gathering Documents"

Hi xxx,

I hope you’re doing well.

I wanted to follow up again regarding my H-1B extension. I still see the status as "gathering documents" in the system, and I haven’t received any updates for over a month.

I fully understand that once the case is filed, it may take ~8 months to get approved — but I believe it’s important that the filing itself happens as soon as possible, especially since I’ve submitted all required documents much earlier this year. My case became eligible for filing on March 30, and it's now already early May.

Also I mentioned previously, I have plans to go abroad in October, so I’ve already flagged the urgency on this. I was told preivously that someone is working on my case, but I haven’t seen any progress. Could you please help confirm that it is being actively handled? And could you let me know the current status and next steps?

I’d really appreciate your help in moving this forward as soon as possible. Thanks again.

Best regards,
Situ


### 05/09

Yes I have a chat with V and x. They just replied and started look into this this morning.

Do you think we should reply what we discussed yesterday?

"

On that day, LION primary exchange was changed several times (LION.N -> LION.OQ -> LION.N -> LION.OQ -> LION.N)

The order that did not trade - its volume aggregator registered to LION.N's container, but at that time, LION.OQ is the correct ric to use to receive MOOP updates. So this order with LION.N is not receiving any volume updates, as a result, has 0 tpc and 0 target qty. Even when LION.OQ changed back to LION.N, a new container is created instead of the original one order regsitered to, so still no volume updates.

We think this happened due to LION's primary exchange changed back and forth in the same day. And we are still trying to find out why DS pulsed out so many updates that day (core issue). On algo side, as Ameya pointed out, there's complexity to handle these types of intraday reference data updates.

If the QV flags order with this problem ....

"

Reply Jeff's LION.OQ order: this order does not have issue, since from it arrives to complete, the LION.OQ was always the correct ric to use, volume can be updated.





"

