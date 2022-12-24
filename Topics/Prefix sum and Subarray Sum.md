如何找到Prefix Sum:
```
        prefix[0] = arr[0]; // for element at index at zero, it is same
        
        // making our prefix array
        for(int i = 1; i < n; i++)
        {
            prefix[i] = arr[i] + prefix[i - 1];
        }
```

如何用Prefix Sum找到 sum 等于 k 的sub array数量:
```
class Solution {
public:
    int subarraySum(vector<int>& arr, int k) {
	    // 创建prefix array
        int n = arr.size();
        
        int prefix[n]; prefix[0] = arr[0];
        for(int i = 1; i < n; i++) 
            prefix[i] = arr[i] + prefix[i - 1];
        
        // 用来记录结果的ans和map
        unordered_map<int,int> mp;
        int ans = 0;
        
        for(int i = 0; i < n; i++) // 遍历prefix array
        {
            if(prefix[i] == k) // if already equal to k, increment ans
                ans++;
            
            // 判断(prefix[i] - k)是否在map里
            if(mp.find(prefix[i] - k) != mp.end())
            {
                ans += mp[prefix[i] - k];
            }
            
            mp[prefix[i]]++; // put prefix sum into our map
        }
        
        return ans;
    }
};
```