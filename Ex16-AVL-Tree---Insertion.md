# Ex16 AVL Tree - Insertion
## DATE:
## AIM:
To write a C function to insert the elements in an AVL Tree.

## Algorithm
1. 
2. 
3. 
4.  
5.   

## Program:
```
/*
Program to insert the elements in an AVL Tree
Developed by: Jwalamukhi S
RegisterNumber: 212223040079
*/
/*typedef struct node
{
int data;
struct node *left,*right;
int ht;
}node;
node *insert(node *,int);
void preorder(node *);
//void inorder(node *);
int height(node *);
node *rotateright(node *);
node *rotateleft(node *);
node *RR(node *);
node *LL(node *);
node *LR(node *);
node *RL(node *);
int BF(node *);
*/ 
node * insert(node *T,int x)
{
    // type your code here
    if(T==NULL)
    {
        T=(node*)malloc(sizeof(node));
        T->data=x;
        T->left=NULL;
        T->right=NULL;
    }else
    
        if(x>T->data)
        {
            T->right=insert(T->right,x);
            if(BF(T)==-2)
            {
                if(x>T->right->data)
                T=RR(T);
                else
                T=RL(T);
                
            }
        }
           
           else
           if(x<T->data)
            {T->left=insert(T->left,x);
            if(BF(T)==2)
            {
                if(x<T->left->data)
                T=LL(T);
                else
                T=LR(T);
                
            }}
            T->ht=height(T);
            return (T);
        }

```

## Output:


![Screenshot 2025-05-21 135940](https://github.com/user-attachments/assets/c5d14a7d-39b1-471d-958c-6d17f522cd1f)

![Screenshot 2025-05-21 135948](https://github.com/user-attachments/assets/e9904e3e-adc4-4819-901f-9c4e1f956d49)


## Result:
Thus, the function to insert the elements in an AVL Tree is implemented successfully in C programming language.
