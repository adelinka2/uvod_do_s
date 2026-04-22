5

```cpp
template<typename T>
class BinaryTree {
private:
    TreeNode<T>* root;

    int countNodes(TreeNode<T>* current) const {
        if (!current) {
            return 0;
        }

        int leftCount = countNodes(current->left);
        int rightCount = countNodes(current->right);

        return leftCount + rightCount + 1;
    }

    bool searchValue(TreeNode<T>* current, const T& val) const {
        if (!current) {
            return false;
        }

        if (current->data == val) {
            return true;
        }

        bool foundLeft = searchValue(current->left, val);
        if (foundLeft) return true;

        return searchValue(current->right, val);
    }

public:
    int size() const {
        return countNodes(root);
    }

    bool contains(const T& value) const {
        return searchValue(root, value);
    }
};
```

9
```cpp
vector<T> inorderTraversal(TreeNode<T>* node) {
    vector<T> output;
    stack<TreeNode<T>*> st;
    TreeNode<T>* ptr = node;

    while (ptr || !st.empty()) {
        if (ptr) {
            st.push(ptr);
            ptr = ptr->left;
        } else {
            TreeNode<T>* temp = st.top();
            st.pop();

            output.push_back(temp->data);

            ptr = temp->right;
        }
    }

    return output;
}
```
