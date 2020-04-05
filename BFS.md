 ## BFS
 BFS is a traversing algorithm where you should start traversing from a selected node (source node) and traverse the graph layer wise thus exploring the neighbor nodes (nodes which are directly connected to source node). You must then move towards the next-level neighbor nodes.

![enter image description here](https://he-s3.s3.amazonaws.com/media/uploads/fdec3c2.jpg)

## Template
 ```java
    void bfs(Graph g, Node start){
	    //hash map to store visited
	    HashSet<Node> visited = new HashMap<>();
	    // init queue
	    Queue<Node> queue = new LinkedList<>();
	    //push start node to the queue
	    queue.offer(start);
	    //bfs
	    while(!queue.isEmpty()){
		    //current level
		    int size = queue.size()
		    while(size > 0){
			    //current node
			    Node n = queue.poll();
			    
			    //do something for current node
			    
			    //add neighbors to queue
			    for(neighbor : neighbors){
			    if(!visited.contains(neighbor){
				    vistied.add(neighbor);
				    queue.offer(neighbor);
			    }
			    size --;
			}
	    }
    }
   ```
   **Complexity**

The time complexity of BFS is  **O(V + E)**, where V is the number of nodes and E is the number of edges.

   ## Examples

**Graph : Leetcode 286 Walls and Gates**

You are given a  _m x n_  2D grid initialized with these three possible values.

1.  `-1`  - A wall or an obstacle.
2.  `0`  - A gate.
3.  `INF`  - Infinity means an empty room. We use the value  `231  - 1 = 2147483647`  to represent  `INF`  as you may assume that the distance to a gate is less than  `2147483647`.

Fill each empty room with the distance to its  _nearest_  gate. If it is impossible to reach a gate, it should be filled with  `INF`.

*Example:*

Given the 2D grid:

INF    -1     0     INF
INF   INF  INF   -1
INF   -1     INF   -1
  0     -1     INF  INF

After running your function, the 2D grid should be:

  3  -1   0   1
  2   2   1  -1
  1  -1   2  -1
  0  -1   3   4



**Approach 1 Brute force:**
The brute force approach is simple, we just implement a breadth-first search from each empty room to its nearest gate.

**Complexity analysis**

-   Time complexity :  O(m^2  n^2). For each point in the  m×n  size grid, the gate could be at most m×n  steps away.
    
-   Space complexity :  O(mn). The space complexity depends on the queue's size. Since we won't insert points that have been visited before into the queue, we insert at most  m × n  points into the queue.

**Approach 2 BFS:**

```java
class Solution {
    public void wallsAndGates(int[][] rooms) {
        // null check
        if(rooms.length == 0 || rooms[0].length == 0) return;
        
        Queue<int[]> queue = new LinkedList<>();
        
        // scan grid
        for(int i = 0; i < rooms.length; i++){
            for(int j = 0; j < rooms[0].length; j++){
            //push gates to queue
                if(rooms[i][j] == 0) queue.offer(new int[]{i,j});
            }
        }
        
        int[][] dirs = {{1,0},{-1,0},{0,1},{0,-1}};
        
        // bfs
        while(!queue.isEmpty()){
            int size = queue.size();
            while(size > 0){
                int[] c = queue.poll();
                for(int[] dir : dirs){
                    int x = c[0] + dir[0];
                    int y = c[1] + dir[1];
                    
                    if(x < 0 || y < 0 || x >= rooms.length || y >= rooms[0].length 
                       || rooms[x][y] <= rooms[c[0]][c[1]] + 1) continue;
                    rooms[x][y] = rooms[c[0]][c[1]] + 1;
                    queue.offer(new int[]{x,y});
                }
                size--;
            }
        }
        return;
    }
}

```
**Complexity analysis**

-   Time complexity :  O(mn). Node: O(mn) Edge:O(mn)
    
-   Space complexity :  O(mn). The space complexity depends on the queue's size. Since we won't insert points that have been visited before into the queue, we insert at most  m × n  points into the queue.

**Similar Questions**

Easy
[Rotting Oranges](https://leetcode.com/problems/rotting-oranges/)

Medium
[Word Ladder](https://leetcode.com/problems/word-ladder/)

Medium
[Number of Islands](https://leetcode.com/problems/number-of-islands/)

Hard
[Robot Room Cleaner](https://leetcode.com/problems/robot-room-cleaner/)



**Tree: Leetcode 103 Binary Tree Zigzag Level Order Traversal**

Given a binary tree, return the zigzag level order traversal of its nodes' values. (ie, from left to right, then right to left for the next level and alternate between).

```java
class Solution {
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        List<List<Integer>> res = new ArrayList<List<Integer>>();
        if(root == null) return res;
        Queue<TreeNode> queue = new LinkedList<TreeNode>();
        queue.offer(root);
        int size = queue.size();
        int l = 1;
        while(!queue.isEmpty()){
            size = queue.size();
            List<Integer> level = new ArrayList<Integer>();
            while(size > 0){
                TreeNode node = queue.poll();
                if(node.left != null) queue.offer(node.left);
                if(node.right != null) queue.offer(node.right);
                if(l%2 == 0) level.add(0,node.val);
                else level.add(node.val);
                size--;
            }
            l++;
            res.add(level);
        }
        return res;
    }
}
```
**Complexity analysis**

**time complexity**: O(n), n is the number of nodes
**Space complexity**: O(n) n is the number of nodes // generally it should be the maximum num of nodes on each level.

**Summary**: the queue order is better to keep the same, from left to right, when you insert element into the array, you can decide the order of it.

**Similar Questions**

Medium
[Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)

Medium
[Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/)
