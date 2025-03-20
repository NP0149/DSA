# Print Max ascii values sum of distinct length substring in a string

# Approach

1)generate all the substrings of string ,select the substrings of distinct length and then find the ascii values of them
return maximum ascii value among them


```
   public static void printascii(String s){
        int n = s.length();
        int sl = 3;
        int maxasc = 0;
        for (int i = 0; i < n - sl + 1; i++) {
            int j = i + sl - 1;
            String m = "";
            for (int k = i; k <= j; k++) {
                m += s.charAt(k);
            }
            if (m.length() == sl) {
                int ascsum = 0;
                for (int t = 0; t < m.length(); t++)
                    ascsum += (int) m.charAt(t);
                maxasc = Math.max(ascsum, maxasc);

            }

        }
        System.out.println("the max ascii sum for length 3=" + maxasc);
    }

```

# Complexities Analysis

time:O(N);

Space:O(1);
