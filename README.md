# -
合并两个从小到大排序的有序链表
#include <stdio.h>
#include <stdlib.h>
typedef struct node
{
    int d;
    struct node * next;
}Node;

Node * creatnode()
{
	int i=0;
	Node *head=NULL;
	Node *p=NULL;
	Node *tail=NULL;
	head=(Node *)malloc(sizeof(Node));
	tail=head;
	while(1)
	{
		p = (Node*)malloc(sizeof(Node));
        scanf("%d",&p->d);
        tail->next = p;
        tail = p;
		tail->next=NULL;
		if(getchar()=='\n')
			break;
	}
	return head;
}
int main()
{
	Node *head1=NULL;
	Node *head2=NULL;
	Node *p1=NULL,*p2=NULL;
	Node *temp=NULL;
	int flag=0;
	head1=creatnode();
	head2=creatnode();
	p1=head1;
	head2=head2->next;
	while(p1->next!=NULL&&head2!=NULL)
	{
		if(head2->d<=p1->next->d)
		{
			temp=head2->next;
			p2=p1->next;
			head2->next=p2;
			p1->next=head2;
			head2=temp;
		}
		p1=p1->next;
	}
	if(head2==NULL)
		flag=1;
	if(flag==0)
		p1->next=head2;
	p1=head1->next;
	while(p1!=NULL)
	{
		printf("%d ",p1->d);
		p1=p1->next;
	}
	printf("\n");
	return 0;
}
