# Median of two sorted arrays

[Problem Link](https://leetcode.com/problems/median-of-two-sorted-arrays/submissions/1694911644/)

# Approach-I

1)take new array and then combine all the elements in the two arrays and then find the meadian by applying formula

2)even number of ele=(n/2)+(n/2-)/2  return arr[ele];

3)for odd return arr[n/2];

```
class Solution {
    public double findMedianSortedArrays(int[] a, int[] b) {
        int n1=a.length;
        int n2=b.length;
    int idx=n1+n2-1;
    int arr[]=new int[n1+n2];
    int i=n1-1;
    int j=n2-1;
    while(i>=0 && j>=0){
        if(a[i]>=b[j]){
            arr[idx--]=a[i--];
        }
        else{
            arr[idx--]=b[j--];
        }
    }
    while(i>=0){
        arr[idx--]=a[i--];
    }
    while(j>=0){
        arr[idx--]=b[j--];
    }
    int n=arr.length;
  int mid1=(n)/2;
  int mid2=mid1-1;
  if((n)%2==0){
    return (arr[mid1]+arr[mid2])/2.0;
  }
  else{
    return arr[mid1];
  }
    }
}
```
# Complexities

Time:O(n1+n2)

Space:O(n1+n2)

# Approach-II

1)calculate index and then increase count with that if you find the count equal to the index then just store it and then calculate the median so,there is no need of extra array

```
class Solution {
    public double findMedianSortedArrays(int[] a, int[] b) {
        int n1=a.length;
        int n2=b.length;
        int n=n1+n2;
        int ind1=n/2;
        int ind2=ind1-1;
        int i=0;
        int j=0;
        int mid1=-1;
        int mid2=-1;
        int count=0;
        while(i<n1 && j<n2){
            if(a[i]<=b[j]){
                if(count==ind1){
                    mid1=a[i];
                }
                if(count==ind2){
                    mid2=a[i];
                }
                i++;
                count++;
            }
            else{
                if(count==ind1){
                    mid1=b[j];
                }
                if(count==ind2){
                    mid2=b[j];
                }
                j++;
                count++;
            }
        }
        while(i<n1){
                  if(count==ind1){
                    mid1=a[i];
                }
                if(count==ind2){
                    mid2=a[i];
                }
                i++;
                count++;
        }
        while(j<n2){
                 if(count==ind1){
                    mid1=b[j];
                }
                if(count==ind2){
                    mid2=b[j];
                }
                j++;
                count++;
        }

    if(n%2==0){
        return (mid1+mid2)/2.0;
    }
    else{
        return mid1;
    }
    }
}
```
# Complexities

Time:O(n1+n2) or O(n)

Space:O(1)//no extra space is used

# Approach-III

```
class Solution {
    public double findMedianSortedArrays(int[] a, int[] b) {
        int n1=a.length;
        int n2=b.length;
        int n=n1+n2;
        if(n1>n2) return findMedianSortedArrays(b,a);
        int left=(n1+n2+1)/2;
        int low=0;
        int high=n1;
        while(low<=high){
            int mid1=(low+high)/2;
            int mid2=left-mid1;
              int l1=Integer.MIN_VALUE;
              double median=-1;
        int l2=Integer.MIN_VALUE;
        int r1=Integer.MAX_VALUE;
        int r2=Integer.MAX_VALUE;
        if(mid1<n1)  r1=a[mid1];
        if(mid2<n2)   r2=b[mid2];
        if(mid1-1>=0)  l1=a[mid1-1];
        if(mid2-1>=0)   l2=b[mid2-1];
        if(l1<=r2 && l2<=r1){
            if(n%2==0){
         median=(Math.max(l1,l2)+Math.min(r1,r2))/2.0;
            return median;
            }
            else{
                median=Math.max(l1,l2);
                return median;
            }
        }
        else{
            if(l1>r2){
                high=mid1-1;
            }
            if(l2>r1){
                low=mid1+1;
            }
        }
        }
        return 0;
    }
}
```

# Complexities

Time:O(log(min(n1,n2)))

Space:O(1)
