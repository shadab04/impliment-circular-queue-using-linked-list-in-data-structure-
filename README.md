# impliment-circular-queue-using-linked-list-in-data-structure-
#include <stdio.h>
#include<stdlib.h>
struct Node
{
    int data;
    struct Node* next;
};
struct Node* front = NULL;
struct Node* rear = NULL;
void enqueue(int x)
{
    struct Node* newnode =
        (struct Node*)malloc(sizeof(struct Node));
    newnode->data=x;
    newnode->next=NULL;
    if(rear== NULL)
    {
        front=rear=newnode;
        rear->next=front;
    }
    else
    {
        rear->next=newnode;
        rear=newnode;
        rear->next=front;
    }
}
void dequeue()
{
    struct Node* temp = front;
    if((front==NULL)&&(rear==NULL))
    {
        printf("\nQueue is empty");
    }
    else if(front==rear)
    {

        front=rear=NULL;


    }

    else

    {
        temp=front;
        front=front->next;

        rear->next=front;

        free(temp);

    }

}
void display()

{

    struct Node* temp = front;

    printf("\n The elements in a Queue are%d : \n");

    if((front==NULL) && (rear==NULL))
    {
        printf("Queue is empty");

    }
    else

    {
        while(temp->next!=front)
        {
            printf("\n%d,", temp->data);

            temp=temp->next;
        }
        printf("\n%d", temp->data);
    }
}

int main()

{
    int choice,x;
    printf("\n1.enqueue\n2.dequeue\n3.display\n4.exit\n");
    while(choice!=4)
    {
        printf("enter your choice:");
        scanf("\n %d",&choice);
        switch(choice)
        {
        case 1:
            printf("enter the value:\n");
            scanf("\n%d",&x);
            enqueue(x);
            break;
        case 2:
            dequeue();
            break;
        case 3:
            display();
            break;
        case 4:
            exit(0);
            break;
        default:
            printf("invalid choice");
        }
    }
}
