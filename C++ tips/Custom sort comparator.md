```
class Solution {
    // 创建Custom Comparator --- 大的在前，小的在后，如果是vector的话记得加&
    struct comp {
        bool operator() (int a, int b) {
            string comb1 = to_string(a) + to_string(b);
            string comb2 = to_string(b) + to_string(a);
            return comb1 > comb2;
        }
    } mycomp;
public:
    string largestNumber(vector<int>& nums) {
        sort(nums.begin(), nums.end(), mycomp);
    }
};
```