1. FairValueAlgos-Common-Auction.md


Find section "## Force Complete in Close Auction"

.... That is,
```
// update this line

$$V_{flaa} = max(0, orderQty - cumTargetVol - ineligibleFillQty - contVolForecast * multiplier *  /rho_{max_i}$$

// add a new line
Where the multiplier is defined by ContinuousVolumeToAuctionMultiplier [@strategy parameter], used to adjust the volume forecast to prevent over-predict.

```

2. FairValueAlgos-WithVolume-Schedule.md

Find section "#### Closing Auction quantity estimation", and add one sentence to the end of first paragraph:

```
......This forcast of \\(contVolForecast\\) uses the gamma model. /* ADD THIS */ Then, the ContinuousVolumeToAuctionMultiplier [@strategy parameter] is applied on the \\(contVolForecast\\) to adjust it
```
