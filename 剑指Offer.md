# 剑指Offer

### 一、二叉树

##### 1、二叉树的深度

输入一棵二叉树的根节点，求该数的深度。

思路：使用递归的思想。

```java
public class TreeDepth {
    public int TreeDepth(TreeNode root) {
        if (root == null) {
            return 0;
        }

        int leftDepth = TreeDepth(root.left);
        int rightDepth = TreeDepth(root.right);

        return leftDepth > rightDepth ? leftDepth + 1 : rightDepth + 1;
    }
}
```

##### 2、二叉树的广度优先遍历

从上往下打印出二叉树的每个节点，同层节点从左至右打印。 

思路：使用队列（先进先出）辅助。

```java
 public ArrayList<Integer> PrintFromTopToBottom(TreeNode root) {

        Queue<TreeNode> queue = new LinkedList<>();
        ArrayList<Integer> arrayList = new ArrayList<>();

        if (root == null) return arrayList;

        queue.offer(root);
        while (!queue.isEmpty()) {
            TreeNode tmp = queue.poll();
            arrayList.add(tmp.val);
            if (tmp.left != null) {
                queue.offer(tmp.left);
            }
            if (tmp.right != null) {
                queue.offer(tmp.right);
            }
        }
        return arrayList;
    }
```

##### 3、二叉树中和为某一值的路径

输入一颗二叉树的跟节点和一个整数，打印出二叉树中结点值的和为输入整数的所有路径。路径定义为从树的根结点开始往下一直到叶结点所经过的结点形成一条路径。 

思路：

```java
private ArrayList<ArrayList<Integer>> listAll = new ArrayList<ArrayList<Integer>>();
    private ArrayList<Integer> list = new ArrayList<>();

    public ArrayList<ArrayList<Integer>> FindPath(TreeNode root, int target) {
        if (root == null) {
            return listAll;
        }

        list.add(root.val);
        target -= root.val;
        if (target == 0 & root.left == null && root.right == null)
            listAll.add(new ArrayList<Integer>(list));
        FindPath(root.left, target);
        FindPath(root.right, target);
        list.remove(list.size() - 1);
        return listAll;

    }
```

