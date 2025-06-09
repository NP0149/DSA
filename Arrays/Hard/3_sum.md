# 3 sum

[Problem Link](https://leetcode.com/problems/3sum/description/)

# Approach-I(Brute force)

1)three loops one in another and then to get unique elements sort the triplet and then add into the set

2)here,we are adding individual lists to the set so syntax is important
 HashSet<List<Integer>> set = new HashSet<>();


```
import java.util.*;

public class prac {
    public static void main(String[] args) {
        HashSet<List<Integer>> set = new HashSet<>();
        int arr[] = {-1, 0, 1, 2, 0, -2};
        int n = arr.length;
        int target = 0;
            for (int i = 0; i < n; i++) {
                for (int j = i + 1; j < n; j++) {
                    for (int k = j + 1; k< n; k++) {
                        if (arr[i] + arr[j] + arr[k] == target) {
                            List<Integer> triplet=new ArrayList<>();

                            triplet.add(arr[i]);
                            triplet.add(arr[j]);
                            triplet.add(arr[k]);
                            Collections.sort(triplet);
                            set.add(triplet);

                        }
                    }
                }
            }
            System.out.println(set);
        }
    }
```

# Complexities

Time:O(n^3);

Space:O(m);//m is the number os unique elements
