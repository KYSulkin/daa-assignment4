### DAA Assignment4 - Report and Defense

##### Problem 1 - Counting Bits **(5 points)**.
- **State:** `dp[i]` = number of 1-bits in `i`.
- **Recurrence:** `dp[i] = dp[i >> 1] + (i & 1)`. Shifting right drops the last bit, which was already counted, so we only add that last bit back.
- **Base:** `dp[0] = 0`.
- **Complexity:** Time O(n), Space O(n) (the output array).

##### Problem 2 - Jump Game **(5 points)**.
- **State:** `dp[i]` = minimum number of jumps needed to reach index `i`.
- **Recurrence:** from every reachable `i`, for `j = 1..nums[i]`: `dp[i+j] = min(dp[i+j], dp[i] + 1)`.
- **Base:** `dp[0] = 0`, all others start at infinity.
- **Answer:** `dp[n-1]`, which is always reachable by the problem's guarantee.
- **Complexity:** Time O(n·k), where k = max jump length (O(n²) worst case). Space O(n).

##### Problem 3 - Min Cost Climbing Stairs **(5 points)**.
- **State:** `dp[i]` = minimum cost to stand on step `i`, where step `n` is the top.
- **Recurrence:** `dp[i] = min(dp[i-1] + cost[i-1], dp[i-2] + cost[i-2])`.
- **Base:** `dp[0] = dp[1] = 0`, since we can start on either step for free.
- **Complexity:** Time O(n), Space O(n).

##### Problem 4 - Longest Increasing Subsequence **(5 points)**.
- **State:** `dp[i]` = length of the longest increasing subsequence ending at `nums[i]`.
- **Recurrence:** `dp[i] = 1 + max(dp[j])` over all `j < i` with `nums[j] < nums[i]`.
- **Base:** `dp[i] = 1`.
- **Answer:** `max(dp)`.
- **Complexity:** Time O(n²), Space O(n).

##### Problem 5 - Longest Common Subsequence **(5 points)**.
- **State:** `dp[i][j]` = LCS of `text1[0..i)` and `text2[0..j)`.
- **Recurrence:** if the characters match, `dp[i-1][j-1] + 1`; otherwise `max(dp[i-1][j], dp[i][j-1])`.
- **Base:** row 0 and column 0 are 0.
- **Complexity:** Time O(m·n), Space O(m·n).

##### Problem 6 - Edit Distance **(5 points)**.
- **State:** `dp[i][j]` = minimum number of operations to turn `word1[0..i)` into `word2[0..j)`.
- **Recurrence:** if the characters match, `dp[i-1][j-1]`; otherwise `1 + min(replace dp[i-1][j-1], delete dp[i-1][j], insert dp[i][j-1])`.
- **Base:** `dp[i][0] = i`, `dp[0][j] = j`.
- **Complexity:** Time O(m·n), Space O(m·n).

##### Problem 7 - Longest Palindromic Subsequence **(5 points)**.
- **State:** `dp[i][j]` = length of the longest palindromic subsequence in `s[i..j]`.
- **Recurrence:** if `s[i] == s[j]`, `dp[i+1][j-1] + 2`; otherwise `max(dp[i+1][j], dp[i][j-1])`.
- **Base:** `dp[i][i] = 1`. Fill with `i` going from n-1 down to 0 and `j` going up.
- **Complexity:** Time O(n²), Space O(n²).

##### Problem 8 - Palindromic Substrings **(5 points)**.
- **State:** `dp[i][j]` = true if `s[i..j]` is a palindrome.
- **Recurrence:** `dp[i][j] = s[i] == s[j] && (j - i < 2 || dp[i+1][j-1])`.
- **Answer:** the number of true cells, counted while filling the table.
- **Complexity:** Time O(n²), Space O(n²).

##### Problem 9 - Maximum Subarray **(5 points)**.
- **State (Kadane):** `cur` = maximum sum of a subarray ending at `i`.
- **Recurrence:** `cur = max(nums[i], cur + nums[i])`, `best = max(best, cur)`.
- **Base:** `cur = best = nums[0]`, which also handles arrays with only negative numbers.
- **Complexity:** Time O(n), Space O(1).

##### Problem 10 - House Robber **(5 points)**.
- **State:** `dp[i]` = maximum money from houses `0..i`.
- **Recurrence:** `dp[i] = max(dp[i-1], dp[i-2] + nums[i])`, meaning we either skip house `i` or rob it.
- **Base:** `dp[0] = nums[0]`, `dp[1] = max(nums[0], nums[1])`.
- **Complexity:** Time O(n), Space O(n).
