# et101-repo

Hi xxx, we need compliance review for my PR that updating QCC test - <link>

This PR, we moved a VWAP QCC behavior test testVWAPVolumeForecastModel to a regular ARE test, no longer QCC. Goal of this test is to verify the usage of gamma model in VWAP order by checking the OPI target quantities always the same the the expected target quatities file. However, the target quantities is closely driven by gamma model and evaluations, so could be sensitive to any related change. We don't think this is suitible for a QCC test.
Therefore, we'll keep the test as an ARE test, but no longer make it a QCC.

The changes to other QCC tests in PR are just adjustments to expected target quantities, due to the change to skip evaluation on command acks that leads to opi frequency change. You can see the change in target quantities is driven by minor changes in the timestamps, no any actual behavior/execution schedule change.

Can you help with review the PR? Let me know if you have any questions.
