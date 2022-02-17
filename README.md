# linked-
#include<stdio.h>
#include<stdlib.h>
struct node
{
        int data;
        struct node* next;
}*newnode,*temp;
struct node* head=NULL;
struct node* tail=NULL;
//Creation of Single Linked list.
void creation()
{
        int ch,value;
        do{
        newnode=(struct node*)malloc(sizeof(struct node));
                printf("enter the value:\n");
                scanf("%d",&value);
                newnode->data=value;
                newnode->next=NULL;
                if(head==NULL)
                {
                        head=newnode;
                        tail=newnode;
                }
                else
                {
                        tail->next=newnode;
                        tail=newnode;
                }
                printf("Press 1 to continue and others to exit\n");
                fflush(stdin);
                scanf("%d",&ch);
        }while(ch==1);
}
//Display of single linked list.
void display()
{
    printf("Required Single linked list is:\n");
        temp=head;
        while(temp!=NULL)
        {
                printf("# %d #",temp->data);
                temp=temp->next;
        }
}
//Insertion of an element at beginning of single linked list.
void insertion_at_beg()
{
    int inserted_value;
    printf("Enter the inserted value to be inserted at beginning position:\n");
    scanf("%d",&inserted_value);
    newnode=(struct node*)malloc(sizeof(struct node));
    if(newnode==NULL)
    {
        printf("Unable to allocate memory.");
    }
    else
    {
        newnode->data=inserted_value;
        newnode->next=head;
        head=newnode;
    }
}
//Insertion of an element at the ending of single linked list.
void insertion_at_end()
{
    int inserted_value;
    printf("Enter the inserted value to be inserted at ending position:\n");
    scanf("%d",&inserted_value);
    newnode=(struct node*)malloc(sizeof(struct node));
    if(newnode==NULL)
    {
        printf("Unable to allocate memory.");
    }
    else
    {
        newnode->data=inserted_value;
        newnode->next=NULL;
        tail->next=newnode;
        tail=newnode;
    }

}
//Insertion of an element at specified position in single linked list.
void insertion_at_pos()
{
    int inserted_value,position;
    temp=head;
    printf("Enter the inserted value to be inserted at specified position:\n");
    scanf("%d",&inserted_value);
    printf("Enter position to be inserted:\n");
    scanf("%d",&position);
    newnode=(struct node*)malloc(sizeof(struct node));
    for(int i=0;i<position-1;i++)
    {
        temp=temp->next;
    }
    newnode->data=inserted_value;
    newnode->next=temp->next;
    temp->next=newnode;
}
//Deletion of an element at the beginning of the single linked list.
void deletion_at_beg()
{
    temp=head;
    head=head->next;
    temp->next=NULL;
}
//Deletion of an element at the ending of the single linked list.
void deletion_at_end()
{
    temp=head;
    while(temp->next!=tail)
    {
        temp=temp->next;
    }
    temp->next=NULL;
    tail=temp;
}
//Deletion of an element at specified position in single linked list.
void deletion_at_pos()
{
    int position;
    printf("Enter position of an element to be deleted:\n");
    scanf("%d",&position);
    temp=head;
    for(int i=0;i<position-1;i++)
    {
        temp=temp->next;
    }
    temp->next=temp->next->next;
}
//To count the number of elements in single linked list.
void count()
{
    int count=0;
        temp=head;
        while(temp!=NULL)
        {
                count++;
                temp=temp->next;
        }
    printf("Number of nodes present in a given single linked list is:%d\n",count);
}
//To reverse the elements of single linked list.
void reverse()
{
    struct node *prevnode,*currentnode,*nextnode;
    prevnode=0;
    currentnode=nextnode=head;
    while(nextnode!=0)
    {
        nextnode=nextnode->next;
        currentnode->next=prevnode;
        prevnode=currentnode;
        currentnode=nextnode;
    }
    head=prevnode;
}
int main()
{
        int choice=0;
        while(choice<11)
        {
            printf("Operations on Single linked list are:\n");
            printf("1.Creation\n");
            printf("2.Display\n");
            printf("3.Insertion at beginning\n");
            printf("4.Insertion at ending\n");
            printf("5.Insertion at specified position\n");
            printf("6.Deletion at beginning\n");
            printf("7.Deletion at ending\n");
            printf("8.Deletion at specified position\n");
            printf("9.To count the number of elements in a Created Single Linked List:\n");
            printf("10.To reverse the elements of a Created single linked list:\n");
            printf("Others:Exit()\n");
            printf("Enter your choice:\n");
            scanf("%d",&choice);
            switch(choice)
            {
                case 1:
                        creation();
                        break;
                case 2:
                        display();
                        break;
                case 3:
                        insertion_at_beg();
                        break;
                case 4:
                        insertion_at_end();
                        break;
                case 5:
                        insertion_at_pos();
                        break;
                case 6:
                        deletion_at_beg();
                        break;
                case 7:
                        deletion_at_end();
                        break;
                case 8:
                        deletion_at_pos();
                        break;
                case 9:
                        count();
                        break;
                case 10:
                        reverse();
                        break;
                default:
                        break;
            }
        }
