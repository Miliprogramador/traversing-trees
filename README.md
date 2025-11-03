#include <stdio.h>
#include <stdlib.h>

// Define a node structure
struct Node {
    int data;
    struct Node *left;
    struct Node *right;
};

// create a new node
struct Node* createNode(int value) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

// Pre-order traversal
void preorder(struct Node* root) {
    if (root == NULL) return;
    printf("%d ", root->data);
    preorder(root->left);
    preorder(root->right);
}

// In-order traversal
void inorder(struct Node* root) {
    if (root == NULL) return;
    inorder(root->left);
    printf("%d ", root->data);
    inorder(root->right);
}

// Post-order traversal
void postorder(struct Node* root) {
    if (root == NULL) return;
    postorder(root->left);
    postorder(root->right);
    printf("%d ", root->data);
}

    void freeTree(struct Node* root) {
    if (root == NULL) return; 
    // free memory 
    freeTree(root->left);
    freeTree(root->right);
    free(root);
}

int main() { // create tree
    struct Node* root = createNode(1);
    root->left = createNode(2);
    root->right = createNode(3);
    root->left->left = createNode(4);
    root->left->right = createNode(5);

    // Print traversals
    printf("Pre-order traversal: ");
    preorder(root);
    printf("\n");

    printf("In-order traversal: ");
    inorder(root);
    printf("\n");

    printf("Post-order traversal: ");
    postorder(root);
    printf("\n");

    freeTree(root);

    return 0;

}
