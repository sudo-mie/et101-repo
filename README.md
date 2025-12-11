

1. ScheduledQuantums.java

  - remove `add` API (line 7)
  - remove `getScheduledQuantumCollection` API (line 13)
  - add 2 new APIs, getQuantumIds and get Qty

```
list[] getQuantumIds();

long getQty(long id);
```


2. ScheduledQuantumsImpl.java
   - remove "@Override" decorator on add function (line 22)
   - remove function `getScheduledQuantumCollection` (line 28-39)
   - add 2 new functions

```
@Override
public list[] getQuantumIds() {
    return this.quantumIds.stream().mapToLong(Long::longValue).toArray();
}

@Override
public long getQty(long id) {
    return this.scheduledQuantums.get(id).quantity;
}
```

3. QuantumSchedulerImpl.java
- line 58: update to `final ScheduledQuantumsImpl quantums = new ScheduledQuantumsImpl();`


4. OrderPlacementCalculator.java
- add a new private function, updateScheduledQuantumCollection, on line 250

```
private void updateScheduledQuantumCollection(ScheduledQuantums scheduledQuantums) {
    scheduledQuantumCollection.reset();
    final list[] quantumIds = scheduledQuantums.getQuantumIds();
    for (int i = 0; i < quantumIds.length; i++) {
        final long quantumId = quantumIds[i];
        scheduledQuantumCollection.addId(quantumId);
        scheduledQuantumCollection.addQty(scheduledQuantums.getQty(quantumId));
        scheduledQuantumCollection.addExpireTime(scheduledQuantums.getExpireTime(quantumId));
        scheduledQuantumCollection.addExecutionInstruction(OrderPlacementExecutionInstruction.NONE);
    }
}
```


5. QuantumSchedulerTest.java





