# leaders in an array

[Problem Link](https://www.geeksforgeeks.org/problems/leaders-in-an-array-1587115620/1)

# Approach-I

1)traverse the array from last ,the rightmost element in the array is the leader of the array
2) we need to add the elements into the array only if they are greater than or equal to leader and everytime we need to update the leader
3)if the array element is not greater than leader then put -1 in it place and add the elements into the array only if value of array ele
not equal to -1

```
class Solution {
    static ArrayList<Integer> leaders(int arr[]) {
        // code here
        int n=arr.length;
        int leader=arr[n-1];
        ArrayList<Integer> al=new ArrayList<>();
        arr[n-1]=leader;
        for(int i=n-2;i>=0;i--){
            if(arr[i]>=leader){
                leader=arr[i];
            }
            else{
                arr[i]=-1;
            }
        }
        for(int i=0;i<n;i++){
            if(arr[i]!=-1){
                al.add(arr[i]);
            }
        }
        return al;
    }
}

```
# Complexties

Time:O(n)//for traversing the array two times but on total it will become O(n)

Space;O(n)//for storing the result in arraylist
