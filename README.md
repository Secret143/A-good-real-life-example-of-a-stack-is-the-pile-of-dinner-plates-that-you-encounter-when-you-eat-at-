#include <limits.h>

#include <stdio.h>
#include <stdlib.h>
Struct Stack {
	Int top;
	Unsigned capacity;
	Int* array;
};
Struct Stack* createStack(unsigned capacity)
{
	Struct Stack* stack = (struct Stack*)malloc(sizeof(struct Stack));
	Stack->capacity = capacity;
	Stack->top = -1;
	Stack->array = (int*)malloc(stack->capacity * sizeof(int));
	Return stack;
}
Int isFull(struct Stack* stack)
{
	Return stack->top == stack->capacity – 1;
}
Int isempty(struct Stack* stack)
{
	Return stack->top == -1;
}
Void push(struct Stack* stack, int item)
{
	If (isFull(stack))
		Return;
	Stack->array[++stack->top] = item;
}
Int pop(struct Stack* stack)
{
	If (isempty(stack))
		Return INT_MIN;
	Return stack->array[stack->top--];
}
Int peek(struct Stack* stack)
{
	If (isempty(stack))
		Return INT_MIN;
	Return stack->array[stack->top];
}
Void deletemid(struct Stack* stack, int n,int curr)
{
If (isempty(stack) || curr == n)
	Return;
Int x =peek(stack);
Pop(stack);
Deletemid(stack, n, curr+1);
If (curr != n/2)
	Push(stack,x);
}
Void insertmid(struct Stack*stack, int n, int curr,int p)
{
    If (isempty(stack) || curr == n)
	Return;
	Int x =peek(stack);
    Pop(stack);
    Insertmid(stack, n, curr+1,p);
    If (curr == n/2-1)
	Push(stack,p);
	Push(stack,x);
}
Int main()
{
	Struct Stack* stack = createStack(100);
	Printf(“Enter no of elements you want to store initially\n”);
	Int n;
	Scanf(“%d”,&n);
	Printf(“Enter the elements\n”);
	Int a[n];
	For(int i=0;i<n;i++)
    {
        Scanf(“%d”,&a[i]);
        Push(stack,a[i]);
    }
    Printf(“Do you wanna insert or delete \n 1: insertion\n 2: deletetion\n”);
    Int t;
    Scanf(“%d”,&t);
    If(t==2)
    Deletemid(stack,n,0);
    Else if(t==1)
    {
        Printf(“Enter the element you want to insert\n”);
        Int p;
        Scanf(“%d”,&p);
        Insertmid(stack,n,0,p);
    }
    Printf(“\nAfter operation\n”);
    While (!isempty(stack))
	{
		Int p=peek(stack);
		Pop(stack);
		Printf(“%d  “,p);
	}
	Return 0;
}
