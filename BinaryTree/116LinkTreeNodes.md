<h1>Solve by preorder traversal

<p>link left side's two child nodes</p>
<p>link right side's two child nodes</p>
<p>link left side's right child node and right side's left child nodes</p>

```java
class Solution {

    public void traverse(Node node1, Node node2) {

        if(node1 == null || node2 == null) {
            return;
        }

        node1.next = node2;

        traverse(node1.left, node1.right);
        traverse(node2.left, node2.right);
        traverse(node1.right, node2.left);
    }

    public Node connect(Node root) {
        if(root == null) {
            return null;
        }

        traverse(root.left, root.right);
        return root;
    }
}
```
