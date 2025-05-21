# Ex17 AVL Tree – Rotation
## DATE:
## AIM:
To write a C function to perform right rotation in an AVL Tree.

## Algorithm
1. 
2. 
3. 
4.  
5.   

## Program:
```
/*
Program to perform right rotation in AVL Tree
Developed by: Jwalamukhi S
RegisterNumber:  212223040079
*/

#include<stdio.h>
#include<stdlib.h>
 
typedef struct node
{
int data;
struct node *left,*right;
int ht;
}node;
node *insert(node *,int);
//node *Delete(node *,int);
void preorder(node *);
//void inorder(node *);
int height( node *);
node *rotateright(node *);
node *rotateleft(node *);
node *RR(node *);
node *LL(node *);
node *LR(node *);
node *RL(node *);
int BF(node *);
 
int main()
{
node *root=NULL;
int x,n,i;
scanf("%d",&n);
//printf("\nEnter tree data:");
root=NULL;
for(i=0;i<n;i++)
{
scanf("%d",&x);
root=insert(root,x);
}
//printf("\nPreorder sequence:\n");
preorder(root);
return 0;
}
 
node * insert(node *T,int x)
{
if(T==NULL)
{
T=(node*)malloc(sizeof(node));
T->data=x;
T->left=NULL;
T->right=NULL;
}
else
if(x > T->data) // insert in right subtree
{
T->right=insert(T->right,x);
if(BF(T)==-2)
{
if(x>T->right->data)
T=RR(T);
else
T=RL(T);
}}
else
if(x<T->data)
{
T->left=insert(T->left,x);
if(BF(T)==2)
{
if(x < T->left->data)
T=LL(T);
else
T=LR(T);
}}
T->ht=height(T);
return(T);
}
 
int height(node *T)
{
int lh,rh;
if(T==NULL)
return(0);
if(T->left==NULL)
lh=0;
else
lh=1+T->left->ht;
if(T->right==NULL)
rh=0;
else
rh=1+T->right->ht;
if(lh>rh)
return(lh);
return(rh);
}
 
node * rotateright(node *x)
{

node *y;
y=x->left;
x->left=y->right;
y->right=x;
x->ht=height(x);
y->ht=height(y);
return y;
}
 
node * rotateleft(node *x)
{
node *y;
y=x->right;
x->right=y->left;
y->left=x;
x->ht=height(x);
y->ht=height(y);
return(y);
}
 
node * RR(node *T)
{
T=rotateleft(T);
return(T);
}
 
node * LL(node *T)
{
T=rotateright(T);
return(T);
}
 
node * LR(node *T)
{
T->left=rotateleft(T->left);
T=rotateright(T);
return(T);
}
 
node * RL(node *T)
{
T->right=rotateright(T->right);
T=rotateleft(T);
return(T);
}
 
int BF(node *T)
{
int lh,rh;
if(T==NULL)
return(0);
 
if(T->left==NULL)
lh=0;
else
lh=1+T->left->ht;
 
if(T->right==NULL)
rh=0;
else
rh=1+T->right->ht;
 
return(lh-rh);
}
 
void preorder(node *T)
{
if(T!=NULL)
{
printf("%d(Bf=%d)",T->data,BF(T));
preorder(T->left);
preorder(T->right);
}
}
 
```

## Output:

![Screenshot 2025-05-21 140918](https://github.com/user-attachments/assets/11d07e70-f64d-40c9-ac6f-895260d1c737)

![Screenshot 2025-05-21 140937](https://github.com/user-attachments/assets/39489c1e-8326-42dd-9329-e8ea08b07616)


## Result:
Thus, the function to perform right rotation in an AVL Tree is implemented successfully.
