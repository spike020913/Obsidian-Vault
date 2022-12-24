```
class Compare {
        public:
            bool operator() (pair<int, int>& a, pair<int, int>& b) {
                if (a.second == b.second) {
	                return a.first < b.first;
                } else {
	                return a.second < b.second;
                }
            }
    };
```