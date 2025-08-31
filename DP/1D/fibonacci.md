# nth Fibonacci  number

# usual version

```
static int fib(int n){
        if(n==0 || n==1){
            return n;
        }
        else return fib(n-1)+fib(n-2);
    }
```
# Complexities

Time:O(n)

Space:O(n)//stack space

# tabulation

```
 //fibonacci number using tabulation
    static int fib_tab(int n){
      int fib[]=new int[10];
      fib[0]=0;
      fib[1]=1;
      for(int i=2;i<10;i++){
          fib[i]=fib[i-1]+fib[i-2];
      }
      return fib[n];
    }
```
# Complexities

Time:O(n)

Space:O(n)

# Memorisation

```
  //fibonacci number using memorization
    static int []fib=new int[10];//global variable
    static int fib_mem(int n){
       fib[0]=0;
       fib[1]=1;
       if(fib[n]!=-1){
           return fib[n];
       }
       if(n==0 || n==1){
           return n;
       }
       else
           return fib[n]=fib_mem(n-1)+fib_mem(n-2);
    }
```

# Complexities

Time:O(n)

Space:O(n)

# The best or optimal approach

```

  //the most optimal approach
    static int fib_opt(int n){
        if(n==0 || n==1){
            return n;
        }
        int prev2=0;
        int prev1=1;
        int curr=0;
        for(int i=2;i<=n;i++){
         curr=prev1+prev2;
         prev2=prev1;
         prev1=curr;
        }
        return prev1;
    }

```

# Complexities

Time:O(n)

Space:O(1) 


