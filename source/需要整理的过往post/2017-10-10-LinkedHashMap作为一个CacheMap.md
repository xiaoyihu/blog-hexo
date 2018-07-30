---
title: 2017-10-10-LinkedHashMap作为一个CacheMap
---

今天我想实现一个定数的map，搜索Java Map的实现类，发现了下面的说明：


url: https://docs.oracle.com/javase/tutorial/collections/implementations/map.html


>LinkedHashMap provides two capabilities that are not available with LinkedHashSet. When you create a LinkedHashMap, you can order it based on key access rather than insertion. In other words, merely looking up the value associated with a key brings that key to the end of the map. Also, LinkedHashMap provides the removeEldestEntry method, which may be overridden to impose a policy for removing stale mappings automatically when new mappings are added to the map. This makes it very easy to implement a custom cache.

>For example, this override will allow the map to grow up to as many as 100 entries and then it will delete the eldest entry each time a new entry is added, maintaining a steady state of 100 entries.

```java
private static final int MAX_ENTRIES = 100;

protected boolean removeEldestEntry(Map.Entry eldest) {
    return size() > MAX_ENTRIES;
}
```
