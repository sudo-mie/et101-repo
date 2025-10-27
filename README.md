

### Muse Signal Frequency and Latency Questions

Hi [Name],

We’re reaching out regarding a few observations about Muse signals on a recent order. In Wasp, we rely on muse signals for volume counting on several flows, such as the gamma model and VWAP LightGBM TPC calculation.

Recently, on an order (<orderId>, date), we noticed that at a given timestamp, there was a significant discrepancy between Muse signals’s cumVolVwapElig and Wasp’s eligVol, which was unexpected. Upon closer inspection, it appears that the Muse signal had a few seconds of delay, as the values aligned closely again after few seconds.

In addition, we checked the BOP records (see attached screenshot), the calcTime for Muse signals seems to update only about every 5 seconds. This 5-second frequency is much slower than we expected. 

Could you please confirm, is the 5-second the actual update frequency? How is this determined, and could there be any latency issues that might explain this delay? We'd greatly appreciate your help investigating this issue. Please feel free to let me know if you need any additional information.

Best,




