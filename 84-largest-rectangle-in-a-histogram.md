# 84.Largest Rectangle in a Histogram

* [https://leetcode.com/problems/largest-rectangle-in-histogram/](https://leetcode.com/problems/largest-rectangle-in-histogram/)

## Concept

* What is the area if i-th rectangle is the max ht ?

```cpp
area = ht[i] * (r - l - 1) [ r = nsr[i], l = nsl[i]]
ans = max(ans, area)
```

## Weapons

* Nearest Smaller to Left & Right
* Standard Code

```cpp
// find the nearest smaller to left
// monotonic stack based solution
vector<int> fnsl(vector<int>& ht){
      int n = ht.size();
      stack<int> s;

      vector<int> nsl(n);
      for(int i = 0; i < n; i++){
          while(!s.empty() and ht[s.top()] >= ht[i])
              s.pop();
          if(s.empty())
              nsl[i] = -1;
          else
              nsl[i] = s.top();

          s.push(i);
      }

      return nsl;
  }
```



