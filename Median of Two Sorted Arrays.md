# Problem

https://leetcode.com/problems/median-of-two-sorted-arrays/

# Final Code - C#

```
public class Solution 
{
    public double FindMedianSortedArrays(int[] nums1, int[] nums2) 
    {
        double medianIndex = (nums1.Length + nums2.Length - 1) / 2.0;
        int median1 = 0, median2 = 0;

        int i = 0, j = 0, maxIndex = nums1.Length + nums2.Length;
        for (int k = 0; k < maxIndex; k++)
        {
            if(nums1.Length > i && (nums2.Length <= j || nums1[i] < nums2[j])) 
            {
                median1 = median2;
                median2 = nums1[i];
                i++;
            } 
            else
            {
                median1 = median2;
                median2 = nums2[j];
                j++;
            }

            if(medianIndex == k) 
            {
                return median2;
            }
            
            if(medianIndex < k) 
            {
                return (median1 + median2) / 2.0;
            }
        }

        throw new Exception("Couldn't calculate the median value");
    }
}
```