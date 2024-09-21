# Cpp_STL_QuickRevision

It contains C++ STLs usage and quick help with easy to understand comments and examples (copy+paste to use). I learned these while solving different kinds of Leetcode Questions.
I will be using "int, string etc" for ease and not complex entities like pairs, structs etc 😉. You can replace it with any data structure If you are confused with the syntax or description, see the example. I am sure that will clear things BECAUSE I have specifically chosen
🔎 "EASY + IMPORTANT + MOST USED" examples. Last but not least, I have added Leetcode Qns also which can be easily solved using STLs

#📝Different ways of using priority_queue (i.e. heap) 🗻
• Default declarations
```
priority_queue<int> pq;                            //creates max-heap
priority_queue<int, vector<int>> pq;               //creates max-heap
```

• writing comparator function for priority_queue
1. Using in-built comparator provided by C++ : 
```
priority_queue<int, vector<int>, greater<int>> pq;  //creates min-heap
priority_queue< pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>> > pq; //min_heap of pairs
priority_queue< pair<int, int>, vector<pair<int, int>>, greater<> > pq;               //min_heap of pairs
```

•
