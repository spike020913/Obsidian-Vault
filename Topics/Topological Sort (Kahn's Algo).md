核心思路: 找不需要prerequisite的，然后一步一步用BFS删

// Leetcode 210
```
class Solution {
public:
    bool canFinish(int n, vector<vector<int>>& pre) {
        // Create adj list
        vector<vector<int>> adj(n, vector<int>());
        vector<int> nodesRequire(n, 0);
        
        // 把所有的课程和其prerequisite加进去
        for (int i = 0; i < pre.size(); i++) {
            adj[pre[i][1]].push_back(pre[i][0]);
            nodesRequire[pre[i][0]]++;
        }

        queue<int> q;
        // 把所有不需要prerequisite的课加进queue
        for (int i = 0; i < n; i++)
            if (nodesRequire[i] == 0) q.push(i);
            
		// 用 BFS把这些课从其他课的prerequisite list里删掉
        while (!q.empty()) {
            int curr = q.front(); q.pop(); n--;
            for (auto next: adj[curr]) {
                nodesRequire[next]--;
                if (nodesRequire[next] == 0) q.push(next);
            }
        }
        // 如果所有课都pop完过一次，那就是都能上玩
        return n == 0;
    }
};
```