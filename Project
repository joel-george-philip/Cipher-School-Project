class Node {
    int key;
    Node left, right;

    public Node(int item) {
        key = item;
        left = right = null;
    }

    // Main method for testing Node class
    public static void main(String[] args) {
        // Create some sample nodes and test functionality
        Node node1 = new Node(10);
        Node node2 = new Node(20);
        Node node3 = new Node(30);

        // Display key values of the nodes
        System.out.println("Node 1 key: " + node1.key);
        System.out.println("Node 2 key: " + node2.key);
        System.out.println("Node 3 key: " + node3.key);
    }
}

class BinarySearchTree {
    Node root;

    BinarySearchTree() {
        root = null;
    }

    void insert(int key) {
        root = insertRec(root, key);
    }

    Node insertRec(Node root, int key) {
        if (root == null) {
            root = new Node(key);
            return root;
        }

        if (key < root.key)
            root.left = insertRec(root.left, key);
        else if (key > root.key)
            root.right = insertRec(root.right, key);

        return root;
    }

    void delete(int key) {
        root = deleteRec(root, key);
    }

    Node deleteRec(Node root, int key) {
        if (root == null)
            return root;

        if (key < root.key)
            root.left = deleteRec(root.left, key);
        else if (key > root.key)
            root.right = deleteRec(root.right, key);
        else {
            if (root.left == null)
                return root.right;
            else if (root.right == null)
                return root.left;

            root.key = minValue(root.right);

            root.right = deleteRec(root.right, root.key);
        }

        return root;
    }

    int minValue(Node root) {
        int minValue = root.key;
        while (root.left != null) {
            minValue = root.left.key;
            root = root.left;
        }
        return minValue;
    }

    void inorder() {
        inorderRec(root);
    }

    void inorderRec(Node root) {
        if (root != null) {
            inorderRec(root.left);
            System.out.print(root.key + " ");
            inorderRec(root.right);
        }
    }

    public static void main(String[] args) {
        BinarySearchTree bst = new BinarySearchTree();

        bst.insert(50);
        bst.insert(30);
        bst.insert(20);
        bst.insert(40);
        bst.insert(70);
        bst.insert(60);
        bst.insert(80);

        System.out.println("Inorder traversal:");
        bst.inorder();

        int searchKey = 70;
        Node result = bst.search(bst.root, searchKey);
        if (result != null)
            System.out.println("\nFound " + searchKey + " in the BST");
        else
            System.out.println("\n" + searchKey + " not found in the BST");

        int deleteKey = 30;
        bst.delete(deleteKey);
        System.out.println("\nAfter deleting " + deleteKey + ", inorder traversal:");
        bst.inorder();
    }

    Node search(Node root, int key) {
        if (root == null || root.key == key)
            return root;

        if (root.key < key)
            return search(root.right, key);

        return search(root.left, key);
    }
}
