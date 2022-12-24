By default, C++ creates a max-heap for priority queue.

If we want to use min-heap, then:

```
priority_queue <int, vector<int>, greater<int>> g = gq;
```
