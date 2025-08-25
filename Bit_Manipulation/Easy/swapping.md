# Swapping two numbers

# Approach-I

```
 public int[] swap(int a, int b) {
        // Your code goes here
        a=a^b;
        b=a^b;
        a=a^b;
        return new int[]{a,b};
    }
```

# Approach-II

```
 static void by_adding(int a,int b){
        a=a+b;
        b=a-b;
        a=a-b;
        System.out.println("after addition");
        System.out.println(a);
        System.out.println(b);
    }
```

# Complexity Analysis

Time:O(1)

Space:O(1)
