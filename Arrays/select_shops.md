[Problem link](https://www.codechef.com/START264D/problems/SHOPS2)


```
import java.util.*;
import java.lang.*;
import java.io.*;

class Codechef
{
	public static void main (String[] args) throws java.lang.Exception
	{
		// your code goes here
		Scanner sc=new Scanner(System.in);
		int t=sc.nextInt();
      for(int i=0;i<t;i++){
          int n=sc.nextInt();
          int d=sc.nextInt();
          int a[]=new int[n];
          int b[]=new int[n];
          int suma=0;
          int sumb=0;
          for(int j=0;j<n;j++){
               a[j]=sc.nextInt();
          }
          for(int j=0;j<n;j++){
              b[j]=sc.nextInt();
          }
          for(int j=0;j<n;j++){
              suma+=a[j];
              sumb+=b[j];
          }
        int visit1=0;
         visit1+=d;
         int visit2=0;
         visit2+=d;
         int shops_2=0;
         shops_2+=2*d;
        for(int k=0;k<n;k++){
            visit1+=a[k];
            visit2+=b[k];
            shops_2+=Math.min(a[k],b[k]);
        }
        int min=Integer.MAX_VALUE;
        min=Math.min(shops_2,Math.min(visit1,visit2));
         System.out.println(min);
      }
	}
}

```
