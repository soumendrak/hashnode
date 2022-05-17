## Python vs Golang vs Rust

## Test scenario

I have taken the [Two sum problem](https://leetcode.com/problems/two-sum/) from Leetcode.

The problem statement:

> Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
> 
> You may assume that each input would have exactly one solution, and you may not use the same element twice.
> 
> You can return the answer in any order. 

> Example 1:
> 
> Input: nums = [2,7,11,15], target = 9
> Output: [0,1]
> Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
> 
> Example 2:
> 
> Input: nums = [3,2,4], target = 6
> Output: [1,2]
> 
> Example 3:
> 
> Input: nums = [3,3], target = 6
> Output: [0,1]
> 
>  
> 
> Constraints:
> 
>     2 <= nums.length <= 104
>     -109 <= nums[i] <= 109
>     -109 <= target <= 109
>     Only one valid answer exists.
>

## Implementation

I have used a hash map to solve this problem across all three languages.


### Python

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hash_table = {}
        for i, num in enumerate(nums):
            target_num = target - num
            if num in hash_table:
                return i, hash_table[num]
            else:
                hash_table[target_num] = i
        return None
```

#### Python stats

- Run time: **40ms**
- Memory usage: **14.5 MB**


### Golang

```Go
func twoSum(nums []int, target int) []int {
    hashMap := make(map[int] int)
    for i := 0; i < len(nums); i++{
        if _, found := hashMap[nums[i]]; found {
            ans := []int{i, hashMap[nums[i]]}
            return ans
        } else {
            hashMap[target- nums[i]]= i
        }
    }
    return nil
}
```

#### Golang stats

- Run time: **4ms**
- Memory usage: **4.3 MB**


### Rust

```rust
use std::collections::HashMap;
impl Solution {
    pub fn two_sum(nums: Vec<i32>, target: i32) -> Vec<i32> {
        let mut hash_table: HashMap<i32, i32> = HashMap::new();
    for i in 0..nums.len() {
        // println!("Processing number: {}", nums[i]);
        match hash_table.get(&nums[i]){
            Some(&x) => return vec![x, i as i32],
            None => hash_table.insert(target - nums[i], i as i32),
        };
    };
    return vec![-1, -1]
    }
}
```

#### Rust stats

- Run time: **2ms**
- Memory usage: **2.2 MB**

## Conclusion

- As per the results, Rust took the least memory and was the fastest of all three.

For more such insights follow me on [Twitter](https://twitter.com/soumendrak_).