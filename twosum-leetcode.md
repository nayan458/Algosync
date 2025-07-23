# Two Sum - LeetCode
  
  ## Problem Description
  
  Can you solve this real interview question? Two Sum - Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.
  
  ### Examples:
  ```
  Example 1:


Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].


Example 2:


Input: nums = [3,2,4], target = 6
Output: [1,2]


Example 3:


Input: nums = [3,3], target = 6
Output: [0,1]
  ```
  
  ### Constraints:
  
  Constraints:

 * 2 <= nums.length <= 104
 * -109 <= nums[i] <= 109
 * -109 <= target <= 109
 * Only one valid answer exists.

 

Follow-up: Can you come up with an algorithm that is less than O(n2) time complexity?
  
  
  ### Approach:
  ---
  
  #### approach 1:
  

  #### Solution Language:
  ```  Java  ```
  ```
  class Solution {

    public static void sortbyColumn(int arr[][], int col)
    {
        // Using built-in sort function Arrays.sort with lambda expressions
      
      Arrays.sort(arr, (a, b) -> Integer.compare(a[col],b[col])); // increasing order
        
    }

    public int[] twoSum(int[] nums, int target) {
        int size = nums.length;
        int arr[][] = new int [size][2];

        for(int i = 0; i < size; i++){
            arr[i][0] = nums[i];
            arr[i][1] = i;
        }

        sortbyColumn(arr,0);

        int beg = 0, end = size - 1;

        while(beg < end){
            int rslt = arr[beg][0] + arr[end][0];
            if( rslt < target)
                ++beg;
            else if( rslt > target)
                --end;
            else
                break;
        }
        int rsltInd[]  = new int[2];
        rsltInd[0] = arr[beg][1];
        rsltInd[1] = arr[end][1];

        return rsltInd;
    }
}
  ```
  