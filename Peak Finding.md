# **Peak Finding**

> QUESTION:
>
> we have been given an array and we have to find the peak element, for example the array is **arr[]={1,2,3,4,5,4,3,2}**, then the **5** is the peak since the number before it are less than **5** and numbers after it are greater..

There are two ways we can solve this question:

1. linear search:

   we will iterate the whole array and find an element which satisfies the condition 

   **arr[i-1]<arr[i]>arr[i+1]**, the arr[i] would be the peak element.

   **Time complexity: ** O(n)

   **space complexity:** O(1)

2.  binary search:

   We would divide the array into two portion, increasing region and decreasing region,

   in 

   *increasing region:* **arr[mid - 1] < arr[mid]**(answer can't be in left side) 

   *decreasing region:* **arr[mid] > arr[mid + 1]**(answer can't be in right side)

   

   

   Using binary search would be better idea, and we will see why.

   while applying binary search we would encounter **3** conditions:

   1) if **arr[mid]>arr[mid+1]** and **arr[mid] > arr[mid-1]**:

      ​	then we would find our peak element **arr[mid]**

   2) if **arr[mid]>arr[mid+1]:**

      ​	then the peak would be **arr[mid]** or any element left to it.

      ​	`end = mid`

   3) if **arr[mid] < arr[mid + 1]:**

      ​	then the peal element would be **arr[mid]** or right to it.

      ​	`start=mid`

      
      **CODE**
      ```java
      public int peakIndexInMountainArray(int[] arr) {
          int start=0;
          int end=arr.length-1;
          while(start<=end){
              int mid=(start+end)/2;
              if(arr[mid]>arr[mid+1] && arr[mid]>arr[mid-1]){
                  return mid;
              }else if(arr[mid]>arr[mid+1]){
                  end=mid;
              }else if(arr[mid]<arr[mid+1]){
                  start=mid;
              }        
          }
      }
      ```

      
