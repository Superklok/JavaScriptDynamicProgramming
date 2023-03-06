# JavaScript Coin Change

## Challenge:

You are given an integer array `coins` representing coins of different denominations and an integer `amount` representing a total amount of money.

Return the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return `-1`.

You may assume that you have an infinite number of each kind of coin.

### 1<sup>st</sup> Example:

`Input: coins = [1,2,5], amount = 11`
<br/>
`Output: 3`
<br/>
`Explanation: 11 = 5 + 5 + 1`

### 2<sup>nd</sup> Example:

`Input: coins = [2], amount = 3`
<br/>
`Output: -1`

### 3<sup>rd</sup> Example:

`Input: coins = [1], amount = 0`
<br/>
`Output: 0`

### Constraints:

`1 <= coins.length <= 12`
<br/>
`1 <= coins[i] <= 2³¹ - 1`
<br/>
`0 <= amount <= 10⁴`

## Solution:

`const coinChange = (coins, amount) => {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const dp = Array(amount + 1).fill(amount + 1);`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`dp[0] = 0;`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`for(let coin of coins) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`for(let i = coin; i <= amount; i++) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`dp[i] = Math.min(dp[i], dp[i - coin] + 1);`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const ans = dp[dp.length - 1];`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return ans == amount + 1 ? -1 : ans;`
<br/>
`};`
<br/>
<br/>