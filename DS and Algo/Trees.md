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

