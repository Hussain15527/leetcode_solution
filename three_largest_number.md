**QUESTION:** find the three largest number in an array without sorting it, and in single pass, i.e. Time: O(n), Space: O(1).

**NOTE: used this approach in question 628. Maximum Product of Three Numbers leetcode**



**SOLUTION** 

We are going to create three variables, say a,b and c and give them minimum possible value any integer could have **```Integer.MIN_VALUE```**

As we traverse through the array ( nums ), 

1) If we find an element ``nums[i]`` which is bigger than **a** (`nums[i]`> a)
   we would update the values of a,b and c in the following way:

   ```
   c=b;
   b=a;
   a=nums[i];
   ```

   

2) if we find an element such that ```a>nums[i]>b```

   ```java
   c=b;
   b=nums[i];
   ```

   

3) if we find an element such that ````a>b>num[i]>c````:

   ```java
   c=nums[i];
   ```



And the complete tranversal the values of a,b and c would be that of first largest, second largest and third largest respectively.

**CODE**

```java
		//creating three varaibles
		int a=Integer.MIN_VALUE;
        int b=Integer.MIN_VALUE;
        int c=Integer.MIN_VALUE;
		//traveral
        for(int i=0;i<nums.length;i++){
            if(nums[i]>a){
                c=b;
                b=a;
                a=nums[i];
            }else if(nums[i]>b){
                c=b;
                b=nums[i];
                    
            }else if(nums[i]>c){
                c=nums[i];
            }
        }
```



