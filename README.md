Query

1. Check pct of parent orders with large gaps; 1) ~14% overall, and 2) generate daily chart
2. Filter child executions with gaps > 1 hr, then group by transition types -> find which transition type caused most of the issue
           - select count i by transition from .data_gaps where max_gap > 01:00:00:000


Page
1. Background

Quantum placement starts from passive posts. The more passive we allocate, the greater potential spread we capture but traded off with a lower probability of executing. Therefore, it is crucial to optimize where it should ideally be allocated. We want to evaluate how quantum placement executes in the past, and investiagte if we need to / how to further improve the spread vs timing tradeoff for passive post phase. 

2. Analysis

add the graph from query 1


