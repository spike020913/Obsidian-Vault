```
class UnionFind {
public:
	// Constructor
	UnionFind(int n) {
        parent = vector<int> (n,0);
        size = vector<int> (n,1);
        for (int node = 0; node < n; node++) {
            parent[node] = node;
        }
    }
    // Find class with pass compression
    int find(int num) {
        if (parent[num] != num) {
	        parent[num] = find(parent[num]);
        }
        return parent[num];
    }

    bool unionS(int A, int B) {
        // Find the roots for A and B.
        int rootA = find(A);
        int rootB = find(B);
        // Check if A and B are already in the same set.
        if (rootA == rootB) {
            return false;
        }
        // We want to ensure the larger set remains the root.
        if (size[rootA] < size[rootB]) {
            // Make rootB the overall root.
            parent[rootA] = rootB;
            // The size of the set rooted at B is the sum of the 2.
            size[rootB] += size[rootA];
        }
        else {
            // Make rootA the overall root.
            parent[rootB] = rootA;
            // The size of the set rooted at A is the sum of the 2.
            size[rootA] += size[rootB];
        }
        return true;
    }
    private:
	    vector<int> parent;
	    vector<int> size;
}; 
```