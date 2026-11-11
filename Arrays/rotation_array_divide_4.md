[Problem Link](https://www.codechef.com/problems/ROT4)


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
     int n=sc.nextInt();
     for(int i=0;i<n;i++){
         int len=sc.nextInt();
         String s=sc.next();
         char arr[]=s.toCharArray();
         int a[]=new int[s.length()];
         for(int k=0;k<s.length();k++){
             a[k]=arr[k]-'0';
         }
         int count=0;
         for(int t=0;t<s.length();t++){
             int x=a[(t+len-2)%len];
             int y=a[(t+len-1)%len];
             int num=x*10+y;
             if(num%4==0){
                 count++;
             }
         }
         System.out.println(count);
     }
	}
}

```
