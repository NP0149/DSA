```
class Solution {
    long power(long x,long y,long mod){
        long ans=1;
        while(y>0){
        if (y % 2 == 1)
       ans = (ans * x) %mod;

          x = (x * x) % mod;

          y = y / 2;
        }
        return ans;
    }
    public int sumDecoded(long[] arr) {
        long sum=0;
        long check = 1000000007L;
        for(int i=0;i<arr.length;i++){
            long width=arr[i]%10;
            long d=arr[i]/10;
            String str=String.valueOf(d);
            long x=Integer.parseInt(str.substring(0,(int)width));
            x=x%check;
            long y=Integer.parseInt(str.substring((int)width,str.length()));
            y=y%check;
            long decoded=power(x,y,check);
            sum+=decoded;
            sum=sum%check;
        }
        return (int)(sum%check);
    }
}
```
