```
class Solution {
public:
    int findKthLargest(vector<int>& nums, int k) {
        int left = 0, right = nums.size() - 1, kth;
		// 左边的都大于nums[idx] 右边的都小于nums[idx]
	    // 在这种情况下idx == k-1时就是Kth largest element
	    
        while (true) {
			// 通过partition出idx
            int idx = partition(nums, left, right);
            if (idx == k - 1) {
                kth = nums[idx];
                break;
            }
            // 如果idx小于k-1,说明pivot的值太大了，需要将pivot的值变小
            if (idx < k - 1) {
                left = idx + 1;
            // 如果idx大于k-1,说明pivot值太小了,要减少比pivot小的值
            } else {
                right = idx - 1;
            }
        }
        return kth;
    }
private:
	// 这里implement是pivot为最左边的partition
    int partition(vector<int>& nums, int left, int right) {
        int pivot = nums[left], l = left + 1, r = right;
        while (l <= r) {
	        // 如果左边比pivot小，右边比pivot大，那么直接swap值
	        // 此时大的值会靠左，小的值靠右
            if (nums[l] < pivot && nums[r] > pivot) {
                swap(nums[l++], nums[r--]);
            }
            // 如果左边比pivot大，正合我意，不用swap了，左边++
            if (nums[l] >= pivot) {
                l++;
            }
            // 如果右边比pivot小，正合我意，不用swap了，右边--
            if (nums[r] <= pivot) {
                r--;
            }
        }
        // 将pivot和right换位置，此时r左边都是比r大的，右边都是比r小的
        swap(nums[left], nums[r]);
        return r;
    }
};
```