
## CS32

### Inorder Tree Traversal

*Contributed by Shirley He*

Given the root pointer to a binary search tree, implement the
following function to print the tree in-order (use recursion):
* `void inOrder(Node* root);`

#### Example

Suppose level order of the tree : A / B C / D E F G / H I J K L 

Inorder : H D I B J E K A L F C G

#### Solution

```cpp
#include <iostream>
using namespace std;

struct Node {
    int key;
    Node* left;
    Node* right;
};

void inOrder(Node* root) {
    if ( root ) {
        inOrder(root->left);
        cout << root->key << " ";
        inOrder(root->right);
    }
}

int main() {
    Node* root;
    root->key = 10;
    root->left = new Node;
    root->left->key = 20;
    root->left->left = nullptr;
    root->left->right = nullptr;
    root->right = nullptr;
    
    inOrder(root);
    return 0;
}


```

---
