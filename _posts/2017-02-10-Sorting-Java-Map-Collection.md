---
layout: post
title: "How to sort Java Map Collection"
date: 2017-02-10
---

Today, I was dealing with another question, and I needed to sort a HashMap in Java. I realized that I've niether tried nor needed sorting
a map in Java!. Then, I decided to work and search on it and write this down in my blog. There is no built-in function to sort a map. 
But, there is a way to sort List interface in Collections API, which is ```java Collections.sort() ```, and there is a way to convert
a map to a List ```List<Map.Entry<String, Integer>> list = new LinkedList<Map.Entry<String, Integer>>(mostFrequentPhrases.entrySet()); ```
Now, let's give a code example:

```java
private static Map<String, Integer> sortMapByValue(Map<String, Integer> mostFrequentPhrases) {
        List<Map.Entry<String, Integer>> list = new LinkedList<Map.Entry<String, Integer>>(mostFrequentPhrases.entrySet());

        // 2. Sort list with Collections.sort(), provide a custom Comparator
        //    Try switch the o1 o2 position for a different order
        Collections.sort(list, (o1, o2) -> (o1.getValue()).compareTo(o2.getValue()));

        Map<String, Integer> sortedMap = new LinkedHashMap<String, Integer>();
        for (Map.Entry<String, Integer> entry : list) {
            sortedMap.put(entry.getKey(), entry.getValue());
        }
        return sortedMap;
    }
```
