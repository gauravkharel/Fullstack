You are a product manager and currently leading a team to develop a new product. Unfortunately, the latest version of your product fails the quality check. Since each version is developed based on the previous version, all the versions after a bad version are also bad.

Suppose you have `n` versions `[1, 2, ..., n]` and you want to find out the first bad one, which causes all the following ones to be bad.

You are given an API `bool isBadVersion(version)` which returns whether `version` is bad. Implement a function to find the first bad version. You should minimize the number of calls to the API.

**Example 1:**

**Input:** n = 5, bad = 4
**Output:** 4
**Explanation:**
call isBadVersion(3) -> false
call isBadVersion(5) -> true
call isBadVersion(4) -> true
Then 4 is the first bad version.

**Example 2:**

**Input:** n = 1, bad = 1
**Output:** 1

**Constraints:**

- `1 <= bad <= n <= 231 - 1`

## Solution
Basically, it find the middle value if the n is or, greater than n. And, checks if it returns false if it returns false, it adds 1 and, checks again. else it just check backward by -1 until it returns true in that way it find the exact bad version.

#1 
```
/**
 * The knows API is defined in the parent class Relation.
 * isBadVersion(version: number): boolean {
 *     ...
 * };
 */

var solution = function(isBadVersion: any) {
    return function(n: number): number {
       let left = 1
       let right = n
        let res = 1
        while(right >= left){
            const mid = Math.floor((right + left)/2)
            if(!isBadVersion(mid)){
                if(isBadVersion(mid+1)){
                    return res = mid + 1
                }
                left = mid+1
                
            }else{
                right = mid -1 
            }            
        }
    return res
    };
};
```