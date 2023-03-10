<p>BruteForce with recuresion DFS</p>
<p>Time complexity: O(k^n)</p>
```java
class Solution {
    public int dp(int[] coins, int amount) {

        if(amount == 0) return 0;
        if(amount < 0) return -1;

        int res = Integer.MAX_VALUE;
        for(int coin : coins) {
            int sub = dp(coins, amount - coin);

            if(sub == -1) continue;

            res = Math.min(res, sub + 1);
        }

        return res == Integer.MAX_VALUE ? -1 : res;

    }

    public int coinChange(int[] coins, int amount) {
        return dp(coins, amount);
    }
}
```

<p>DFS with memo</p>
<p>Time Complexity: O(kn) k refer to the number of the coin, n refer to number of subquestions</p>
```java
class Solution {
    int[] memo;

    public int coinChange(int[] coins, int amount) {
        memo = new int[amount + 1];
        // 备忘录初始化为一个不会被取到的特殊值，代表还未被计算
        Arrays.fill(memo, -666);

        return dp(coins, amount);
    }

    public int dp(int[] coins, int amount) {
        int[] temp = memo;
        if (amount == 0) return 0;
        if (amount < 0) return -1;
        // 查备忘录，防止重复计算
        if (memo[amount] != -666)
            return memo[amount];

        int res = Integer.MAX_VALUE;
        for (int coin : coins) {
            // 计算子问题的结果
            int subProblem = dp(coins, amount - coin);
            // 子问题无解则跳过
            if (subProblem == -1) continue;
            // 在子问题中选择最优解，然后加一
            res = Math.min(res, subProblem + 1);
        }
        // 把计算结果存入备忘录
        memo[amount] = (res == Integer.MAX_VALUE) ? -1 : res;
        return memo[amount];
    }
}
```

<p>DP iteration with array</p>
<p>Time Complexity: O(kn) k refer to the number of the coin, n refer to number of subquestions</p>
```java
class Solution {
    public int coinChange(int[] coins, int amount) {
        int[] dp = new int[amount + 1]; //该数组是用来记录0-11每个金额下需要的最少硬币数量
        // 数组大小为 amount + 1，初始值也为 amount + 1
        Arrays.fill(dp, amount + 1);

        // base case
        dp[0] = 0;
        // 外层 for 循环在遍历所有状态的所有取值
        for (int i = 0; i < dp.length; i++) {
            // 内层 for 循环在求所有选择的最小值
            for (int coin : coins) {
                // 子问题无解，跳过
                if (i - coin < 0) {
                    continue;
                }
                dp[i] = Math.min(dp[i], 1 + dp[i - coin]);
            }
        }
        return (dp[amount] == amount + 1) ? -1 : dp[amount];
    }
}
```
