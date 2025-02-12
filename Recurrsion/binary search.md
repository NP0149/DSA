# Binary search using recurrsion 


```Java
class main{
 public static void main(String args[]){
 Scanner sc=new Scanner(System.in);
 int arr[]={1,2,3,4,5,6};
 System.out.println("enter the number that u wanna search in a array");
 int target=sc.nextInt();
 int s=0;//start
 int e=arr.length-1;//end
 System.out.println(search(arr,target,s,e));
 }
 static int search(int arr[],int target,int s,int e){
  if(s>e){
   return -1;
   }
   int m=s+(e-s)/2;
   if(arr[m]==target){
 return m;
 }
 if(arr[m]>target){
 return search(arr,target,s,m-1);
 }
  return search(arr,target,m+1,e);
  }
  }
 ```
