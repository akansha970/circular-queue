# circular-queue
#include<stdio.h>
#include<conio.h>
#define size 20
int queue[size];
int front=-1;
int rear=-1;


int is_empty()
{
    if(front==-1)
    {
	return 1;
    }
    else
    {
	return 0;
    }
}

int Stack_Full()
{
    if((front==rear+1) || (front==0 && rear==size-1))
    {
	return 1;
    }
    else
    {
	return 0;
    }
}

void enqueue(int x)
{
    if(Stack_Full())
    {
	printf("queue is full/n");
    }
    else if(front==-1)
    {
	front=0;
	rear=0;
    }
    else
    {
	rear=(rear+1)%size;
    }
    queue[rear]=x;
}

void dequeue()
{
    if(is_empty())
    {
	printf("queue is empty");
    }
    else if(front==rear)
    {
	front=-1;
	rear=-1;
    }
    else
    {
	printf("element bing removed is %d\n",queue[front]);
	front=(front+1)%size;
    }

}

void display()
{           int i=0;
    if(is_empty())
    {
	printf("queue is empty\n");
    }
    else
    {
	printf("queue is \n");
	for(i=front;i<=rear;i=(i+1)%size)
	{
	    printf("%d\t",queue[i]);
	}
    }
}

void main()
{
    int choice,x;
    while(1)
    {
	printf("MAIN MENU\n");
	printf("1.enqueue\n");
	printf("2.dequeue\n");
	printf("3.display\n");
	printf("4.exit\n");
	printf("please enter one of the above options\n");
	scanf("%d",&choice);
	switch(choice)
	{
	    case(1) : printf("enter the value to be inserted ");
		      scanf("%d",&x);
		      enqueue(x);
		      break;

	    case(2) : dequeue();
		      break;

	    case(3) : display();
		      break;

	    case(4) : exit(0);

	    default : printf("invalid choice\n");
		      break;
	}
    }
}
