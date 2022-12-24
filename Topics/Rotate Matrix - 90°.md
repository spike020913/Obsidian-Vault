核心思路：先transpose，再reverse each row
```
void rotate(vector<vector<int>>& matrix) {
		// Transpose the matrix
        int n = matrix.size();
        // loop all rows
        for(int i=0; i<n; ++i) {
	        // start from diagonal line
            for(int j=i; j<n; ++j) {
	            // swap
                swap(matrix[i][j], matrix[j][i]);
            }
        }
		// 把每一行reverse一遍
        for(int i=0; i<n; ++i) {
            int left = 0, right = n-1;
            while(left < right) {
                swap(matrix[i][left], matrix[i][right]);
                ++left;
                --right;
            }
        }
    }
```