# Ex22 Searching for a Book ID in a Binary Search Tree (BST)
## DATE: 20-02-2026
## AIM:
To design and implement java program that constructs a Binary Search Tree (BST) using given Book IDs and checks whether a specific Book ID exists in the BST.

## Algorithm

1. Start
2. Read number of elements (n)
3. Create an empty Binary Search Tree (BST)
4. For each element:
5. Insert the element into the BST
6. Read number of queries (q)
7. For each query:
8. Read the key to search
9. If root is null, return false
10.If key equals root data, return true
11.If key is less than root data, search in left subtree
12.Else search in right subtree
13.Print "Found" if true, otherwise print "Not Found"
14. Stop   

## Program:
``` JAVA
/*
Program to constructs a Binary Search Tree (BST) using given Book IDs 
Developed by: DILLI PRATHAP
RegisterNumber:  212224110014 
*/

import java.util.*;

public class BookIDSearch {
static class Node {
int data;
Node left, right;
Node(int data) {
this.data = data;
}
}

public static Node insert(Node root, int key) {
if (root == null) return new Node(key);
if (key < root.data) root.left = insert(root.left, key);
else root.right = insert(root.right, key);
return root;
}

public static boolean search(Node root, int key) {
if (root == null) return false;
if (root.data == key) return true;
if (key < root.data) return search(root.left, key);
else return search(root.right, key);
}

public static void main(String[] args) {
Scanner sc = new Scanner(System.in);
int n = sc.nextInt();
Node root = null;
for (int i = 0; i < n; i++) {
root = insert(root, sc.nextInt());
}
int q = sc.nextInt();
while (q-- > 0) {
int key = sc.nextInt();
System.out.println(search(root, key) ? "Found" : "Not Found");
}
}
}
```

## Output:

<img width="426" height="184" alt="516889859-a3c0ff0c-41e3-411f-b0ce-8c2efd4b8864" src="https://github.com/user-attachments/assets/5fa7f82e-6192-4b7d-8e22-992b64152593" />


## Result:
The program has been successfully implemented and executed.
It constructs a Binary Search Tree from the given Book IDs and accurately determines whether a queried Book ID exists in the library system.
