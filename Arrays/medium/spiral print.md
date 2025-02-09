# Spiral Print

[problem link](https://leetcode.com/problems/spiral-matrix/description/)

```Java
lass Solution {
    public List<Integer> spiralOrder(int[][] arr) {
        int n=arr.length;
        int m=arr[0].length;
 int minr=0;
  int maxr=n-1;
  int minc=0;
  int maxc=m-1;
  int tne=m*n;
  int count=0;
  List<Integer> l=new ArrayList<Integer>();
  try{
  while(count<tne){
    for(int j=minc;j<=maxc && count<tne;j++){
        l.add(arr[minr][j])
;
count++;
}
minr++;
for(int i=minr;i<=maxr && count<tne;i++){
l.add(arr[i][maxc]);
count++;
}
maxc--;
for(int j=maxc;j>=minc && count<tne;j--){
 l.add(arr[maxr][j]);
 count++;
 }
 maxr--;
 for(int i=maxr;i>=minr && count<tne;i--){
 l.add(arr[i][minc]);
 count++;
 }
 minc++;
 }
 }
 catch(Exception e){
}
return l;
 }
```
# complexity analysis
 time complexity:O(N)
 space complexity:O(1)
 
