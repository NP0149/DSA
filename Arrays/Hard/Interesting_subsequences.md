# Interesting subsequences

```
import java.util.*;

public class Interesting {
    static long nCr(int n, int r) {
        if (r > n) return 0;
        long res = 1;
        for (int i = 1; i <= r; i++) {
            res = res * (n - i + 1) / i;
        }
        return res;
    }

    static void find(int arr[], int k) {
        Arrays.sort(arr);
        int minSum = 0;
        for (int i = 0; i < k; i++) {
            minSum += arr[i];
        }

        int kthValue = arr[k - 1];
        int totalKthValueCount = 0;
        int neededKthValueCount = 0;

        for (int x : arr) {
            if (x == kthValue) totalKthValueCount++;
        }
        for (int i = 0; i < k; i++) {
            if (arr[i] == kthValue) neededKthValueCount++;
        }

        long ways = nCr(totalKthValueCount, neededKthValueCount);
        System.out.println(ways);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int k = sc.nextInt();
        int[] arr = new int[n];
        for (int i = 0; i < n; i++) arr[i] = sc.nextInt();
        find(arr, k);
    }
}

```
