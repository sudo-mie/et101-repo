QuantumSchedulerTest

update scheduledQuantums.add(1, expireTimeEpoch1) 

line 277-278:

```
scheduledQuantums.setScheduledQuantumsCollection(scheduledQuantumsOutput.getScheduledQuantumsCollection());
```

line 444:

```
scheduledQuantums.setScheduledQuantumsCollection(scheduledQuantumsOutput.getScheduledQuantumsCollection());
```



Note: if test did not pass, try using this instead:

```
ScheduledQuantumsCollectionImpl testScheduledQuantums = new ScheduledQuantumsCollectionImpl();
testScheduledQuantums.addId(1);
testScheduledQuantums.addExpireTime(expireTimeEpoch1);
testScheduledQuantums.addId(2);
testScheduledQuantums.addExpireTime(expireTimeEpoch1);
scheduledQuantums.setScheduledQuantumsCollection(testScheduledQuantums);
```


