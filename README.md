# et101-repo



### 05/21

If we don't cache, the value used by feature calculation would be getInterpolatedLookBackValueFromNow(time_of_calculation) and the journal value will be getInterpolatedLookBackValueFromNow(time_of_journal).
Even though in the same evaluation, the time_of_calculation and time_of_journal may be different, and thus may have different value? I think ideally we should journal exactly the value we used in volume surprise calculation.





"

