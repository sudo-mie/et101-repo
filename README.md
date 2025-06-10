# et101-repo


Documentation

- should we also reference this new doc in the FairValueAlgos-VWAP-Schedule.md, where other TPC calculation methods are discussed

ARE

Test.java

- line 263: we can define this new column name as a static string in this file and use it for adding/verifying the column
- line 53: for this test the minimum duration of LGBM is what being tested, so instead of comparing with order 1 where LGBM not enabled at all, I think it makes more sense to combine with the "amendExtendExpireTimeTrigger" test case, and directly comparing lgbm order with amended duration < min duration vs > min duration in one test
