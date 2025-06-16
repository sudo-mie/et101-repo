# et101-repo


This test is a duplicate of the test above (testCloseAuctionQtyCappedByOrderQtyMinusTarget), it is created just for "CLOSE" because it will fail the above test if not hardcoding shouldEvalOnCommandAck to true. Now we fixed the above test, so that CLOSE can also pass with shouldEvalOnCommandAck as false. So now we can remove this duplicated test and add back "CLOSE" to the original test

