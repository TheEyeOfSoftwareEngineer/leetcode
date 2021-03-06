## 47-全排列II
给定一个可包含重复数字的序列 nums ，按任意顺序 返回所有不重复的全排列。

示例 1：
```
输入：nums = [1,1,2]
输出：
[[1,1,2],
 [1,2,1],
 [2,1,1]]
```

示例 2：
```
输入：nums = [1,2,3]
输出：[[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

提示：
```
1 <= nums.length <= 8
-10 <= nums[i] <= 10
```

### java
```java
class Solution {

    public List<List<Integer>> permuteUnique(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        if(nums == null || nums.length == 0) return ans;
        Arrays.sort(nums);
        dfs(ans, nums.length, nums, new ArrayList<Integer>(), new boolean[nums.length]);
        return ans;
    }

    private void dfs(List<List<Integer>> ans, int n, int[] nums, List<Integer> path, boolean[] visited) {
        if(path.size() == n) {            
            ans.add(new ArrayList<>(path));
            return;
        }

        for( int i = 0; i < nums.length; i++) {
            if(visited[i] || (i > 0 && nums[i-1] == nums[i] && !visited[i-1])) continue;
            visited[i] = true;
            path.add(nums[i]);
            dfs(ans, n, nums, path, visited);
            visited[i] = false;
            path.remove(path.size()-1);
        }
    }
}
```