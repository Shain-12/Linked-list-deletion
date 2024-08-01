#include<stdio.h>
#include<stdlib.h>
struct node
{
    int data;
    struct NODE *next;    
};
void linkedlistTraversal(struct node *ptr){
    while (ptr!=NULL)
    {
        printf("element: %d\n",ptr->data);
       ptr= ptr->next;      
    }   
}
// Case 1: Deleting the first element from the linked list
struct node * deleteFirst(struct node * head){
    struct node * ptr = head;
    head = head->next;
    free(ptr);
    return head;
}
struct node * deleteAtIndex(struct node * head,int index){
    struct node * ptr = head;
    struct node * qtr=ptr->next;
    int i=0;
    //shifting the pointers
    while (i!=index-1)
    {
        ptr=ptr->next;
        qtr=qtr->next;
    }
    ptr->next=qtr->next;
    free(qtr);   
    return head;
}
struct node * deleteAtEnd(struct node * head){
    struct node * ptr = head;
    struct node * qtr=ptr->next;   
    //shifting the pointers
    while (qtr->next!=NULL)
    {
        ptr=ptr->next;
        qtr=qtr->next;  
    }
    ptr->next=NULL;
    free(qtr);    
    return head;
}
//deleting the element with a given value from the linked list
struct node * deleteAtValue(struct node * head,int value){
    struct node * ptr = head;
    struct node * qtr=ptr->next;    
    //shifting the pointers
    while (qtr->next!=NULL && qtr->data!=value)
    {
        ptr=ptr->next;
        qtr=qtr->next;
    }
    if (qtr->data==value)
    {
ptr->next=qtr->next;
    free(qtr);  
    }    
    return head;
}
int main(){
    struct node *head;
        struct node *second;
    struct node *third;
        struct node *fourth;
//allocated in heap section
    head=(struct NODE *)malloc(sizeof(struct node));
        second=(struct NODE *)malloc(sizeof(struct node));
    third=(struct NODE *)malloc(sizeof(struct node));
        fourth=(struct NODE *)malloc(sizeof(struct node));
//linking first and second nodes
head->data=7;
head->next=second;
//linking second and third nodes
second->data=13;
second->next=third;
//link the  3rd  and 4th node
third->data=67;
third->next=fourth;
fourth->data=42;
fourth->next=NULL;
printf("linked list before deletion is:\n");
linkedlistTraversal(head);
head=deleteFirst(head);
printf("linked list after at 1st deletion is:\n");
linkedlistTraversal(head);
head=deleteAtIndex(head,1);
printf("linked list after at an index deletion is:\n");
linkedlistTraversal(head);
head=deleteAtEnd(head);
printf("linked list after end node  deletion is:\n");
linkedlistTraversal(head);
printf("linkedlist after deletion at value is\n");
head=deleteAtValue(head,13);
linkedlistTraversal(head);
    return 0;
}
