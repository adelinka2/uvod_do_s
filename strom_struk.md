5

```cpp
template<typename T>
class BinaryTree {
private:
    TreeNode<T>* root;

    // TODO 1: Spočítaj počet uzlov rekurzívne
    int sizeHelper(TreeNode<T>* node) const {
        if (node == nullptr) return 0;

        return 1 + sizeHelper(node->left) + sizeHelper(node->right);
    }

    // TODO 2: Zisti, či strom obsahuje hodnotu
    bool containsHelper(TreeNode<T>* node, T value) const {
        if (node == nullptr) return false;

        if (node->data == value) return true;

        return containsHelper(node->left, value) || containsHelper(node->right, value);
    }

public:
    int size() const { return sizeHelper(root); }
    bool contains(T value) const { return containsHelper(root, value); }
};
```

9
```cpp
// In-order traversal iteratívne
vector<T> inorder(TreeNode<T>* root) {
    vector<T> result;
    stack<TreeNode<T>*> s;
    TreeNode<T>* current = root;

    while (current != nullptr || !s.empty()) {
        // Choď čo najďalej vľavo
        while (current != nullptr) {
            s.push(current);
            current = current->left;
        }

        // Spracuj uzol
        current = s.top();
        s.pop();
        result.push_back(current->data);

        // Prejdi na pravý podstrom
        current = current->right;
    }

    return result;
}
```
