![[Pasted image 20240906135722.png]]

```
a tree

node<T>
value: T
children: []


a binary tree is bit different, here it is
binary tree node<T>
value : T
left: 
right: 
so, the traversal happen in the way given below:
```

Trees Traversal:
This is the one important thing to understand trees DS. 
Here's the link
https://leetcode.com/discuss/study-guide/1212004/Binary-Trees-study-guide

Trees Traversal basically is visiting every node in the tree.
There's 3 different ways to do that in a binary tree. 
by 1. recurseLeft 2. recurseRight 3. post order recursion
![[Pasted image 20240907094321.png]]
Steps usually involves: visitNode() which recurse in the given three ways. 
In postOrder, the tree is already traverse. 
![[trees traversal.excalidraw]]


#### Binary Trees
- binary tree and traversal order
- sub-tree operations: first, successor, insert, delete
- set binary tree (BST -> Binary Search Tree)
- sequence binary tree in sub-tree size augmentation

-> Binary Trees (nodes | items | links)
![[binary tree struc]]
-> Binary tree example
![[binary tree example]]

-> Subtree (x)

```
// JavaScript implementation of tree using array
// numbering starting from 0 to n-1.
const tree = Array(10).fill(null);

function root(key) {
	if (tree[0] != null) {
		console.log("Tree already had root");
	} else {
		tree[0] = key;
	}
}

function setLeft(key, parent) {
	if (tree[parent] == null) {
		console.log(`Can't set child at ${(parent * 2) + 1}, no parent found <br>`);
	} else {
		tree[(parent * 2) + 1] = key;
	}
}

function setRight(key, parent) {
	if (tree[parent] == null) {
		console.log(`Can't set child at ${(parent * 2) + 2}, no parent found <br>`);
	} else {
		tree[(parent * 2) + 2] = key;
	}
}

function printTree() {
	for (let i = 0; i < 10; i++) {
		if (tree[i] != null) {
			console.log(tree[i]);
		} else {
			console.log("-");
		}
	}
}

// Driver Code
root("A");
setLeft("B", 0);
setRight("C", 0);
setLeft("D", 1);
setRight("E", 1);
setRight("F", 2);
printTree();



// This code is contributed by lokeshpotta20

```
