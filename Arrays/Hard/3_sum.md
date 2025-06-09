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



# Approach-II

1)the third element becomes -(arr[i]+arr[j]),store it in temp and then check if that is present in the array


```
class Solution {
    public List<List<Integer>> threeSum(int[] arr) {
        List<List<Integer>> li = new ArrayList<>();
        int n = arr.length;
        HashSet<List<Integer>> hs = new HashSet<>();
        HashMap<Integer, Integer> hm = new HashMap<>();

        for (int i = 0; i < n; i++) {
            hm.put(arr[i], hm.getOrDefault(arr[i], 0) + 1);
        }

        if (arr.length == 3) {
            if (arr[0] + arr[1] + arr[2] == 0) {
                List<Integer> l = Arrays.asList(arr[0], arr[1], arr[2]);
                Collections.sort(l);
                hs.add(l);
            }
        }

        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                int temp = -1 * (arr[i] + arr[j]);
                if (hm.containsKey(temp)) {
                    int count = 0;
                    if (arr[i] == temp) count++;
                    if (arr[j] == temp) count++;
                    if (hm.get(temp) > count) {
                        List<Integer> l = Arrays.asList(arr[i], arr[j], temp);
                        Collections.sort(l);
                        hs.add(l);
                    }
                }
            }
        }

        li.addAll(hs);
        return li;
    }
}

```

# Compelxities

Time:O(n^2)

Space:O(n^2)//hashset of triplets
