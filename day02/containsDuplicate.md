# Contains Duplicate

## Brute Force Method
- Compare every element with every other element in the array to check if any value appears more than once.
- Iterate through the array. For each index i:
  - Run another loop from index i+1 to n-1 (let this index be j).
  - Check if nums[i] is equal to nums[j].
  - If they are equal, return true since a duplicate exists.
- If all pairs are checked and no equal elements are found, return false.
- **Time Complexity:** O(N²).
- **Space Complexity:** O(1).

## Better Method 
- If the array is sorted first, duplicate elements will appear next to each other. Instead of checking all pairs, we only need to compare adjacent elements.
- Sort the array.
- Iterate through the array from index 0 to n-2.
  - For each index i, compare nums[i] with nums[i+1].
  - If both values are equal, return true since a duplicate exists.
- If the traversal finishes without finding equal adjacent elements, return false.
- **Time Complexity:** O(NlogN) + O(N) = O(NlogN).
- **Space Complexity:** O(1).

## Optimal Method
- Use set data structure to keep track of elements that have already been seen.
- Traverse the array once.
  - For each element, check if it already exists in the set.
  - If it exists, return true since the element has appeared before.
  - Otherwise insert the element into the set.
- If the traversal finishes without encountering any repeated element, return false.
- **Time Complexity:** O(N).
- **Space Complexity:** O(N).

## Code
```

bool containsDuplicate(vector<int>& nums) {
  unordered_set<int> s;
  for(int i=0;i<nums.size();i++){
    if(s.find(nums[i])!=s.end()) return true;
    s.insert(nums[i]);
  }
  return false;
}

```
