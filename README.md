# binarysearch
class Node:
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None

def insert(root, data):
    """Function to insert data into the binary search tree"""
    if root is None:
        return Node(data)
    if data < root.data:
        root.left = insert(root.left, data)
    else:
        root.right = insert(root.right, data)
    return root

def lca(root, v1, v2):
    """Function to find the Lowest Common Ancestor (LCA) of two nodes in a BST"""
    if not root:
        return None
    
   
    if root.data > v1 and root.data > v2:
        return lca(root.left, v1, v2)
    
    
    if root.data < v1 and root.data < v2:
        return lca(root.right, v1, v2)
    
    
    return root



def main():
    
    values = [4, 2, 3, 1, 7, 6]
    
    
    root = None
    for value in values:
        root = insert(root, value)
    
    
    v1, v2 = 1, 7
    ancestor = lca(root, v1, v2)
    
    if ancestor:
        print(f"The LCA of {v1} and {v2} is: {ancestor.data}")
    else:
        print("LCA not found.")


main()
