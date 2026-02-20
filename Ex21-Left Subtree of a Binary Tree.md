# Ex21 Count the Number of Nodes in the Left Subtree of a Binary Tree
## DATE: 20-02-2026
## AIM:
To design and implement a java program that constructs a binary tree from given level order input and counts the number of nodes present in the left subtree of the root node

## Algorithm

1. Start
2. Read number of elements (n)
3. Input array elements
4. Build a binary tree using level order insertion:
5. Create root node with first element
6. Use a queue to insert left and right children sequentially
7. If root.left is null, print 0
8. Else count number of nodes in left subtree using recursion:
9. If node is null, return 0
10. Return 1 + countNodes(left) + countNodes(right)
11. Display the count
12. Stop   

## Program:
``` JAVA
/*
Program to constructs a binary tree from given level order input and counts the number of nodes 
Developed by: DILLI PRATHAP
RegisterNumber:  212224110014  
*/

import java.util.*;

class Node {
int data;
Node left, right;
Node(int data) {
this.data = data;
this.left = this.right = null;
}
}

public class Main {
static Node buildTree(int[] arr) {
if (arr.length == 0) return null;
Node root = new Node(arr[0]);
Queue<Node> q = new LinkedList<>();
q.add(root);
int i = 1;

while (!q.isEmpty() && i < arr.length) {
Node current = q.poll();
if (i < arr.length) {
current.left = new Node(arr[i++]);
q.add(current.left);
}
if (i < arr.length) {
current.right = new Node(arr[i++]);
q.add(current.right);
}
}

return root;
}

static int countNodes(Node root) {
if (root == null) return 0;
return 1 + countNodes(root.left) + countNodes(root.right);
}

public static void main(String[] args) {
Scanner sc = new Scanner(System.in);
int n = sc.nextInt();
int[] arr = new int[n];
for (int i = 0; i < n; i++) arr[i] = sc.nextInt();
Node root = buildTree(arr);

if (root.left == null) {
System.out.println(0);
} else {
System.out.println(countNodes(root.left));
}
}
}
```

## Output:

<img width="321" height="115" alt="516889081-0b16d2fe-dfed-468c-b6ed-7eb550b9f4fb" src="https://github.com/user-attachments/assets/5810b93e-e5ca-47bf-8d01-21dd4d3d265c" />


## Result:
The program has been successfully implemented and executed.
It correctly constructs the binary tree from level order input and counts the number of nodes in the left subtree of the root node.
