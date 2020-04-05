# Best time to buy and sell stock
## https://leetcode.com/problems/best-time-to-buy-and-sell-stock

Say you have an array for which the ith element is the price of a given stock on day i.

If you were only permitted to complete at most one transaction (i.e., buy one and sell one share of the stock), design an algorithm to find the maximum profit.

**Note that you cannot sell a stock before you buy one.**
```
Example 1:

Input: [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
             Not 7-1 = 6, as selling price needs to be larger than buying price.

Example 2:

Input: [7,6,4,3,1]
Output: 0
Explanation: In this case, no transaction is done, i.e. max profit = 0.
```

# Implementation 1 : O(n^2)
```java
class Solution {
    public int maxProfit(int[] prices) {
        if(prices == null || prices.length <= 1)
            return 0;
        int maxProfit = 0;
        for(int i = 0; i < prices.length - 1; i++) {
            for(int j = i+1; j < prices.length; j++) {
                maxProfit = Math.max(maxProfit, prices[j] - prices[i]);
            }
        }
        return maxProfit;
    }
}
```

# Implementation 2 : O(n)

Say the given array is:

[7, 1, 5, 3, 6, 4]

If we plot the numbers of the given array on a graph, we get:
![Best time to buy and sell stock](best-time-to-buy-and-sell-stock.png?raw=true "Best time to buy and sell stock")

```java
class Solution {
    public int maxProfit(int[] prices) {
        if(prices == null || prices.length <= 1)
            return 0;
        int maxProfit = 0;
        int minPrice = prices[0];
        for(int i = 1; i < prices.length; i++) {
            if(prices[i] < minPrice)
                minPrice = prices[i];
            else
                maxProfit = Math.max(maxProfit, prices[i] - minPrice);
        }
        return maxProfit;
    }
}
```
# Tip :
Make a dotted graph representation for better visualization, this helps in solving the problem.

# References :
1. https://leetcode.com/articles/best-time-to-buy-and-sell-stock
2. https://www.youtube.com/watch?v=mj7N8pLCJ6w
