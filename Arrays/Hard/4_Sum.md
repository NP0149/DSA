# 4 Sum

[Problem Link](https://leetcode.com/problems/4sum/submissions/1661650433/)

# Approach-I(Brute Force)

```
    public static List<List<Integer>> find(int nums[]){
        int n=nums.length;
        Set<List<Integer>> hs=new HashSet<>();
        for(int i=0;i<n;i++){
            for(int j=i+1;j<n;j++){
                for(int k=j+1;k<n;k++){
                   for(int l=k+1;l<n;l++){
                    int sum=nums[i]+nums[j]+nums[k];
                    if(sum==0){
                        List<Integer> temp=Arrays.asList(nums[i],nums[j],nums[k]);
                        Collections.sort(temp);
                        hs.add(temp);
                    }
                }
            }}
        }
        return new ArrayList<>(hs);
    }

```
## Complexities

Time:O(n^4)

Space:O(k)//k unique number of triplets

# Approach-II(optimal)

```
class Solution {
    public List<List<Integer>> fourSum(int[] arr, int target) {
        Arrays.sort(arr);
        int n=arr.length;

        HashMap<Integer,Integer> hm=new HashMap<>();
        for(int i=0;i<n;i++){
            hm.put(arr[i],hm.getOrDefault(arr[i],0)+1);
        }
        List<List<Integer>> li=new ArrayList<>();
        HashSet<List<Integer>> hs=new HashSet<>();
        for(int i=0;i<arr.length;i++){
            if(i>0 && arr[i]==arr[i-1]) continue;
            for(int j=i+1;j<n;j++){
                if(j>i+1 && arr[j]==arr[j-1]) continue;
                for(int k=j+1;k<n;k++){
                    if(k>j+1 && arr[k]==arr[k-1]) continue;
                 long sum = (long)arr[i] + (long)arr[j] + (long)arr[k];
                    long need = (long)target - sum;

                    // need must fit in int and exist in map
                    if (need < Integer.MIN_VALUE || need > Integer.MAX_VALUE) continue;
                    int val = (int)need;

                    int count=0;
                  if(hm.containsKey(val)){
                  if(arr[i]==val) count++;
                  if(arr[j]==val) count++;
                  if(arr[k]==val) count++;
                  if(hm.get(val)>count){
                    List<Integer> l=new ArrayList<>();
                    l.add(arr[i]);
                    l.add(arr[j]);
                    l.add(arr[k]);
                    l.add(val);
                    Collections.sort(l);
                    hs.add(l);
                  }
                  }
                }
            }
        }
        li.addAll(hs);
        return li;
    }
}
    
```

# Complexities

Time:O(n^3)//three fixed loops

Space:O(n^3)//for Set<List<Integer>> and for temporary set O(n)

     


# Approach-III(Efficient)

```
 class Solution {
    public List<List<Integer>> fourSum(int[] arr, int target) {
        int n=arr.length;
        Arrays.sort(arr);
        Set<List<Integer>> st=new HashSet<>();
        for(int i=0;i<n;i++){
            if(i>0 && arr[i]==arr[i-1]) {
            continue;
            }
            for(int j=i+1;j<n;j++){
                if(j>i+1 && arr[j]==arr[j-1]) {
                    continue;
                }
                int k=j+1;
                   int l=n-1;
                   while(k<l){
                    long sum=arr[i];
                    sum+=arr[j];
                    sum+=arr[k]+arr[l];
                   if(sum==target){
                    List<Integer> temp=Arrays.asList(arr[i],arr[j],arr[k],arr[l]);
                     st.add(temp);
                     k++;
                     l--;
                     while(k<l && arr[k]==arr[k-1]) k++;
                       while(k<l && arr[l]==arr[l+1]) l--;
                   }
                   else if(sum<target) k++;
                   else l--;
                   }

                }
            }
        return new ArrayList<>(st);
    }
}
```
# Complexities

Time:O(n^3);

Space:o(k);
