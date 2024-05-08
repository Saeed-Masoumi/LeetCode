# Two Sum
## Difficulty: Easy

### Description:
Given an array of integers *nums* and an integer *target*, return *indices* of the two numbers such that they add up to *target*.  
You may assume that each input would have **exactly one solution**, and you may not use the same element twice.  
You can return the answer in any order.
#### Examples:
>Input: nums = [2,7,11,15], target = 9  
Output: [0,1]  
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].

> Input: nums = [3,2,4], target = 6  
Output: [1,2]  

>Input: nums = [3,3], target = 6  
Output: [0,1]

#### Constraints:

+ 2 <= nums.length <= 104  
+ -109 <= nums[i] <= 109  
+ -109 <= target <= 109  
+ **Only one valid answer exists.**

#### Follow-up:
Can you come up with an algorithm that is less than O(n2) time complexity?

___

### Solution(s):
1. Brute Force   
Time complexity: O(n<sup>2</sup>)   
Space complexity: O(1)
```
for i = 0 to count of numbers do:
	for j = i to count of numbers do:
		if nums[i]+nums[j] = target then return i,j
```
2. Hash Table  
Time complexity: O(n)   
Space complexity: O(n)
```
set map[number,index]
for i = 0 to count of numbers do:
	current_number = element i of numbers
	look_for = target - current_number
	if the map contains look_for then return its index and i, if not add current_number and i to the map

```
## C-Sharp  
```
static int[] TwoSum_BruteForce(int[] nums, int target)
        {
            for (int i = 0; i < nums.Length; i++)
            {
                for (int j = i + 1; j < nums.Length; j++)
                {
                    if (nums[i] + nums[j] == target)
                        return new int[] { i, j };
                }
            }
            return new int[0];
        }
        
        
static int[] TwoSum_HashTable(int[] nums, int target)
        {
            Dictionary<int, int> map = new Dictionary<int, int>(0);
            for (int i = 0; i < nums.Length; i++)
            {
                int look_for = target - nums[i];
                if (map.ContainsKey(look_for))
                {
                    return new int[] { map[look_for], i };
                }
                map[nums[i]] = i;
            }
            return new int[0];
        }
```
## Javascript  
```
const TwoSum_BruteForce = (nums, target) => {
    for (let i = 0; i < nums.length; i++)
        for (let j = i + 1; j < nums.length; j++)
            if (nums[i] + nums[j] == target)
                return Array(i, j);
    return Array();
};


const TwoSum_HashTable = (nums, target) => {
    const map = new Map();
    for (let i = 0; i < nums.length; i++) {
        let look_for = target - nums[i];
        if (map.has(look_for))
            return Array(map.get(look_for), i);
        map.set(nums[i], i);
    }
    return Array();
};
```
## C++
```
#include <iostream>
#include <vector>
#include <map>

const std::vector<int> TwoSum_BruteForce(const std::vector<int> &nums, const int target)
{
    for (int i = 0; i < nums.size(); i++)
        for (int j = i + 1; j < nums.size(); j++)
            if (nums[i] + nums[j] == target)
                return std::vector<int>{i, j};
    return std::vector<int>{};
}

//-std=c++11
const std::vector<int> TwoSum_HashTable(const std::vector<int> &nums, const int target)
{
    std::map<int, int> map;
    for (int i = 0; i < nums.size(); i++)
    {
        int look_for = target - nums[i];
        if (map.count(look_for))
            return std::vector<int>{map[look_for], i};
        map[nums[i]] = i;
    }
    return std::vector<int>{};
}

//-std=c++20
const std::vector<int> TwoSum_HashTable(const std::vector<int> &nums, const int target)
{
    std::map<int, int> map;
    for (int i = 0; i < nums.size(); i++)
    {
        int look_for = target - nums[i];
        if (map.contains(look_for))
            return std::vector<int>{map[look_for], i};
        map[nums[i]] = i;
    }
    return std::vector<int>{};
}
```
## PHP
```
function TwoSum_BruteForce($nums,$target){
	for ( $i = 0; $i < sizeof($nums); $i++)
	{
		for ( $j = $i + 1; $j < sizeof($nums); $j++)
		{
			if ($nums[$i] + $nums[$j] == $target)
				return array( $i, $j );
		}
	}
	return array();
}

function TwoSum_HashTable($nums,$target){
	$map = array();
	for ( $i = 0; $i < sizeof($nums); $i++)
	{
		$look_for = $target - $nums[$i];
		if(array_key_exists($look_for,$map))
			return array($map[$look_for], $i );
        $map[$nums[$i]] = $i;
	}
	return array();
}
```