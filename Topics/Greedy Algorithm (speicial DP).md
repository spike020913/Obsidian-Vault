核心思路：
![[Pasted image 20221110000334.png]]
Example1: Jump Game --- 永远跳最远
```
class Solution {
public:
    bool canJump(vector<int>& nums) {
      int n = nums.size(), farest = 0;
      for(int i = 0;i < n; i++)
      {
        if(farest < i) return false;
        farest = max(i + nums[i], farest);
      }
      
      return true;
    }
};
```

Example2: Meeting Room --- 扫描线
![[Pasted image 20221116181725.png]]
```
while (left < intervals.size() && right < intervals.size()) {
            if (begin[left] < end[right]) {
                left++;
                count++;
            } else {
                count--;
                right++;
            }
            res = max(count, res);
        }
        return res;
```