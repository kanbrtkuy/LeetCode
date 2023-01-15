```java
public class Codec {
// Encodes a tree to a single string.
    String NULL = "#";
    String SEP = ",";
    public String serialize(TreeNode root) {
        StringBuilder sb = new StringBuilder();
        serializeHelp(root, sb);
        return sb.toString();
    }

    public void serializeHelp(TreeNode root, StringBuilder sb) {
        if (root == null) {
            sb.append(NULL).append(SEP);
            return;
        }
        sb.append(root.val).append(SEP);
        serializeHelp(root.left, sb);
        serializeHelp(root.right, sb);
    }

    // Decodes your encoded data to tree.
    public TreeNode deserialize(String data) {
        if (data.length() == 0) {
            return null;
        }
        String[] nodes = data.split(",");
        TreeNode root = deserializeHello(nodes);
        return root;
    }

    int nodesStart = 0;
    public TreeNode deserializeHello(String[] nodes) {
        if (nodesStart > nodes.length) {
            return null;
        }
        if (nodes[nodesStart].equals("#")) {
            nodesStart++;
            return null;
        }
        int rootVal = new Integer(nodes[nodesStart]);
        nodesStart++;
        TreeNode root = new TreeNode(rootVal);
        root.left = deserializeHello(nodes);
        root.right = deserializeHello(nodes);
        return root;
    }
}
```
