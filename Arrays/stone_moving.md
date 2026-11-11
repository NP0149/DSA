[Problem Link](https://www.codechef.com/problems/STONEMOV)


```
import java.util.*;
import java.lang.*;
import java.io.*;

class Codechef
{
    static long find(int arr[]){
      long sum=0;
      int carry=0;
      int diff[]=new int[arr.length+1];
      for(int i=0;i<arr.length-1;i++){
          carry+=diff[i];
          int curr=carry+arr[i];
          int x=Math.min(arr.length-1-i,curr);
          sum+=x;
          diff[i+1]++;
          diff[i+x+1]--;
      }
      return sum;
    }
	public static void main (String[] args) throws java.lang.Exception
	{
	    Scanner sc=new Scanner(System.in);
	int n=sc.nextInt();
    for(int i=0;i<n;i++){
        int m=sc.nextInt();
        int a[]=new int[m];
        for(int t=0;t<m;t++){
            a[t]=sc.nextInt();
        }
        System.out.println(find(a));
    }
	}
}

```
