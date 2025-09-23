# et101-repo


1. line 22

Better to rename it as arrivalPrice to be clear?

2. line 25

The get target price part is the same as else, I think it is cleaner to write as `if (effectiveTime <= continuousStartTime && PriceUtil.isPriceValid(open)) {arrival = open} else {arrival = getTargetPrice(...)} 

3. line 47

Use double //?

4. line 69
  
Would it be better to rename as usePriceWithFallback?


