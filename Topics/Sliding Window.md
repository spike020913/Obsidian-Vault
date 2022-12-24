核心思路: 找不需要prerequisite的，然后一步一步用BFS删

// Leetcode 424
class Solution {
public:
    int characterReplacement(string s, int k) {
        unordered_map<char, int> window;
        int left = 0;
        int currMax = 0, maxChar = 0;
        string str = "";
        // 放大窗口
        for (int right = 0; right < s.length(); right++) {
            window[s[right]]++;
            if(maxChar < window[s[right]]){
                maxChar = window[s[right]];
            }
            //缩小窗口
            while(right - left + 1 - maxChar > k) {
                window[s[left]]--;
                left++;
            }
            currMax = max(currMax, right - left + 1);
        }
        return currMax;
    }
};