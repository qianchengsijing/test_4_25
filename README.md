# test_4_25
#include <stdio.h>
#include <stdlib.h>
typedef struct DNode
{
	int data;
	struct DNode* prior,*next;
}DNode,*DLinklist;
//双链表的初始化
bool Initlist(DLinklist &L)
{
	L = (DNode*)malloc(sizeof(DNode));
	if(L == NULL)
		return false;
	L->prior = NULL;
	L->next = NULL;
	return true;
}
//判断双链表是否为空
bool Empty(DLinklist &L)
{
	if(L->next == NULL)
		return true;
	else
		return false;
}
//按位序插入
bool ListInsert(DLinklist &L,int i,int e)
{
	if(i<1)
		return false;
	DNode* p;
	int j = 0;
	p = L;
	while(p != NULL && j<i-1)
	{
		p = p->next;
		j++;
	}
	if(p == NULL)
		return false;
	DNode* s = (DNode*)malloc(sizeof(DNode));
	s->data = e;
	s->next = p->next;
	if(p->next != NULL)
		p->next->prior = s;
	s->prior = p;
	p->next = s;
	return true;
}
//双链表的插入(指定结点后插）
bool InsertNextDNode(DNode* p,DNode* s)
{
	if(p == NULL || s == NULL)
		return false;
	s->next = p->next;
	if(p->next != NULL)
		p->next->prior = s;
	s->prior = p;
	p->next = s;
	return true;
}
//指定结点前插
bool InsertPriorDNode(DNode* p,DNode* s)
{
	if(p == NULL || s == NULL)
		return false;
	s->next = p->next;
	if(p->next != NULL)
		p->next->prior = s;
	s->data = p->data;
	p->data = s->data;
	s->prior = p;
	p->next = s;
	return true;
}
//双链表的删除（删除后继结点）
bool DeleteNextDNode(DNode* p)
{
	if(p == NULL)
		return false;
	DNode* s = p->next;
	if(s == NULL)
		return false;
	p->next = s->next;
	if(s->next != NULL)
		s->next->prior = p;
	free(s);
	return true;
}
//删除前继结点
bool DeleteNextDNode(DNode* p)
{
	if(p == NULL)
		return false;
	DNode* s = p->prior;
	if(s == NULL)
		return false;
	s->next = p->next;
	if(p->next != NULL)
		p->next->prior = s;
	s->data = p;
	free(p);
	return true;
}
//销毁一个双链表
void DestoryList(DLinklist &L)
{
	while(L->next != NULL)
		DeleteNextDNode(L);
	free(L);
	L = NULL;
}//双链表的遍历
//向后
while(p != NULL)
	p = p->next;
//向前
while(p != NULL)
	p = p->prior;
while(p->prior != NULL)
	p = p->prior;
//循环链表
//循环单链表
typedef struct LNode
{
	int data;
	struct LNode* next;
}LNode,*Linklist;
bool InitList(Linklist &L)
{
	L = (LNode*)malloc(sizeof(LNode));
	if(L == NULL)
		return false;
	L->next = L;
	return true;
}
//判断p结点是否为表尾结点
bool isTail(Linklist L,LNode* p)
{
	if(p->next == L)
		return true;
	else
		return false;
}
//循环双链表
typedef struct DNode
{
	int data;
	struct DNode* prior,* next;
}LNode,*Linklist;
bool InitList(Linklist &L)
{
	L = (LNode*)malloc(sizeof(LNode));
	if(L == NULL)
		return false;
	L->prior = L;
	L->next = L;
	return true;
}
//静态链表
//第一种
#define MaxSize 10
struct Node
{
	int data;
	int next;
};
void testSLinklist()
{
	struct Node a[MaxSize];//a为一个10个Node型元素的数组
}
//第二种
#define MaxSize 10
typedef struct
{
	int data;
	int next;
}SLinklist[MaxSize];
void testSLinklist()
{
	SLinklist a;//a为一个有10个Node型元素数组的静态链表
}
void testSLinklist()
{
	struct Node s;
	printf("sizes=%d\n",sizeof(s));//8

	struct Node a[MaxSize];
	printf("sizea=%d\n",sizeof(a));//80

	SLinklist b;
	printf("sizeb=%d\n",sizeof(b));//80
}
