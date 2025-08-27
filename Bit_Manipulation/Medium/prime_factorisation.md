# Prime Factorisation

# Approach-I

1)consider a element of an array if that is prime just add that also in to the list 

2)consider n as array element and traverse through the <=sqrt(n) and among them find the divisors add n%i and n/i

3)every add list to big list

```
import java.util.*;
public class prime {
 static boolean isprime(int n){
     int count=0;
     for(int i=2;i<=Math.sqrt(n);i++){
         if(n%i==0)
         count++;
     }
     if(count>0){
         return false;
     }
     return true;
 }
  static List<List<Integer>> find_all(int arr[]) {
      List<List<Integer>> al = new ArrayList<>();
      for (int j = 0; j < arr.length; j++) {
          int n = arr[j];
        List<Integer> li=new ArrayList<>();
          if(isprime(n)){
              li.add(n);
          }
          for (int i = 2; i <=Math.sqrt(n); i++) {
              if (n % i == 0) {

                  if (isprime(i)) ;
                  li.add(i);
                  if(isprime(n/i)){
                      li.add(n/i);
                  }
              }
          }
          al.add(li);
      }
          return al;
  }
    public static void main(String[] args) {
     int arr[]={2,3,4,6};
        List<List<Integer>> m=find_all(arr);
        System.out.println(m);
    }
}
```
# Complexities

Time:O(m*n) 

Space:O(m*sqrt(n))
