# Product of Array Except Self

## Brute Force Method
- For each element, we compute the product of all other elements in the array except the current one. Create a result array of the same size as the input array.
- Iterate through the array. For each i:
  - Initialize a variable product = 1.
  - Run another loop from index 0 to n-1 (let this index be j).
  - If j is not equal to i, multiply product with nums[j].
- Store the value of product in result[i].
- **Time Complexity:** O(N²).
- **Space Complexity:** O(N).

## Better Method 
- Instead of recomputing the product for each element, we can precompute the product of elements to the left and the product of elements to the right of each index. Then multiply these two values to get the result.
- Create two arrays:
  - prefix array to store product of elements before each index.
  - suffix array to store product of elements after each index.
- Compute the final result using result[i] = prefix[i] * suffix[i].
- **Time Complexity:** O(N) 
- **Space Complexity:** O(N)

## Optimal Method
- We can store the prefix products directly in the result array and then multiply them with suffix products while traversing from the end.
- Create a result array of size n. In the first pass from left to right:
  - result[0] = 1
  - For each index i from 1 to n-1
    result[i] = result[i-1] * nums[i-1]
- Second pass (right to left):
  - Maintain a variable suffix = 1.
  - Traverse from n-1 to 0.
  - Multiply result[i] with suffix.
  - Update suffix = suffix * nums[i].
- **Time Complexity:** O(N) 
- **Space Complexity:** O(1) (excluding the output array).

## Code
```
vector<int> productExceptSelf(vector<int>& nums) {
    int n = nums.size();
    vector<int> ans(n);
    ans[0] = 1;

    for(int i=1;i<n;i++){
        ans[i] = ans[i-1] * nums[i-1];
    }

    int suf = 1;
    for(int i=n-1;i>=0;i--){
        ans[i] = ans[i] * suf;
        suf = suf * nums[i];
    }

    return ans;
}
```
