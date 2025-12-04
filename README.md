QuantumSchedulerTest

update scheduledQuantums.add(1, expireTimeEpoch1) to

```
scheduledQuantums.getSchduledQuantumsCollection().addId(1);
scheduledQuantums.getSchduledQuantumsCollection().addExpireTime(expireTimeEpoch1);
```

e.g. for order 2

```
scheduledQuantums.getSchduledQuantumsCollection().addId(2);
scheduledQuantums.getSchduledQuantumsCollection().addExpireTime(expireTimeEpoch2);
```
