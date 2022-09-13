#include<stdio.h>
#include <stdlib.h>

struct link_list
{
    int item;
    struct link_list *next;
};

struct link_list *read=NULL;
struct link_list *write=NULL;
int size=NULL; //buffer size
static int p_size=0; //present size of buffer

void enqueue()
{
    int value;
    struct link_list *newnode=(struct link_list*)malloc(sizeof(struct link_list));
    printf("Enter new value : \n");
    scanf("%d",&value);
    newnode->item=value;
    newnode->next=NULL;

    if(read==NULL&&write==NULL)
    {
    read=write=newnode;
        p_size++;
    }
    else
    {   
        if (p_size<size)
        {
            printf("still buffer not filled\n");
            write->next=newnode;
            write=newnode;
            p_size++;
        }
        else
        {
            printf("size is exceeded\n");
            write=write->next;
            read->item=value;
            read=read->next;
        }
        write->next=read;
    }
    write->next=read;
}


void dequeue()
{
    int val;
    struct link_list *ptr=read;
    if(read==NULL)
    {
        printf("Stack is empty \n");
    }
    else
    {
        if (p_size>0)
        {   
            val=read->item;
            read=read->next;
            free(ptr);
            p_size--;
            printf("removed %d\n",val);
        }
        else 
        {
            p_size=0;
            read=write=NULL;
            printf("nothing else to remove\n");
        }
    }   
}


void print()
{
    printf("psize= %d\n",p_size);
    struct link_list *ptr=read;
    if (read==NULL)
    {
        printf("nothing in queue\n");return;
    }
    if (p_size==0) 
    {
        printf("stack empty\n");
        return;
    }
    else
    {
        while (ptr!=NULL)
        {
            if (ptr!=write)
            {
                printf("Value= %d Aderss= %p Next Address= %p\n", ptr->item,ptr, ptr->next);
                ptr=ptr->next;
            }
            else
            {
                printf("Value= %d Aderss= %p Next Address= %p\n", ptr->item,ptr, ptr->next);
                break;
            }
        }
        printf("read--@Value= %d Aderss= %p Next Address= %p\n", read->item,read, read->next);
        printf("write--@Value= %d Aderss= %p Next Address= %p\n", write->item,write, write->next);

    }
}


void main()
{
    char ch;
    int val;
    int loop=1;
    printf("enter the buffer size---\n");
    scanf("%d",&size);
    while(loop==1)
    {
        printf("select a) to add to queue, b) to dequeue s) sort p) print x)ext\n");
        scanf("%c",&ch);
        switch(ch)
        {
            case 'a':
                enqueue();
                break;
            case 'b':
                dequeue();
                break;
            case 'p':
                print();
                break;
            case 'x':
                loop=0;
                break;
        }
    }
}
