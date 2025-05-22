# Ex20 AVL Tree - Deletion
## DATE:
## AIM:
To write a C function to delete an element from an AVL Tree.
## Algorithm

1.Search for the node to delete starting from the root.

2.Delete the node using standard BST rules.

3.Update the height of the affected nodes.

4.Calculate the balance factor of each updated node.

5.Perform rotations if the node is unbalanced.

6.Continue until the tree is balanced again.

## Program:
```
/*

Developed by: Jwalamukhi S
RegisterNumber:  212223040079
*/


typedef struct node
{
int data;
struct node *left,*right;
int ht;
}node;
 
node *insert(node *,int);
node *Delete(node *,int);
void preorder(node *);
void inorder(node *);
int height( node *);
node *rotateright(node *);
node *rotateleft(node *);
node *RR(node *);
node *LL(node *);
node *LR(node *);
node *RL(node *);
int BF(node *);
node * Delete(node *T,int x)
{
    node *p;
    if(T==NULL){
        return NULL;
    }
    else if(x > T->data){
        T->right = Delete(T->right,x);
        if(BF(T)==2){
            if(BF(T->left)>=0){
                T=LL(T);
            }
            else{
                T=LR(T);
            }
        }
    }
    else{
        if(x < T->data){
            T->left=Delete(T->left,x);
            if(BF(T)==-2){
                if(BF(T->right)<=0){
                    T=RR(T);
                }
                else{
                    T=RL(T);
                }
            }
        }
        else{
            if(T->right!=NULL){
                p=T->right;
                while(p->left!=NULL){
                    p=T->left;
                }
                T->data=p->data;
                T->right=Delete(T->right,p->data);
                {
                    if(BF(T)==2){
                        if(BF(T->left)>=0){
                            T=LL(T);
                        }
                        else{
                            T=LR(T);
                        }
                    }
                }
            }
            else{
                return(T->left);
            }
        }
    }
    T->ht = height(T);
    return (T);
}


```

## Output:

![image](https://github.com/user-attachments/assets/ad7db629-4c7b-4b54-917c-de9534669277)


## Result:
Thus, the C program to delete an element from an AVL Tree is implemented successfully.
