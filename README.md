# G-lab



```

#include<stdio.h>

#include<string.h>

#define operand(x) (x>='a' && x<='z' || x>='A' && x<='Z' || x>='0' && x<='9')

char infix[30],postfix[30],stack[30];

int top,i=0;

void init()

{

top=-1;

}

void push(char x)

{

stack[++top]=x;

}

char pop()

{

return(stack[top--]);

}

int isp(char x)

{

int y;

y=(x=='('?0:x=='^'?4:x=='*'?2:x=='/'?2:x=='+'?1:x=='-'?1:x==')'?6:-1);

return y;

}

int icp(char x)

{

int y;

y=(x=='('?4:x=='^'?4:x=='*'?2:x=='/'?2:x=='+'?1:x=='-'?1:x==')'?6:-1);

return y;

}

void infixtopostfix()

{

int j,n=0;

char x,y;

stack[++top]='\0';

for (j=0; (x=infix[i++])!='\0'; j--)

if (operand(x))

postfix[n++]=x;

else

if (x==')')

while ((y=pop())!='(')

postfix[n++]=y;

else

{

while (isp(stack[top])>=icp(x))

postfix[n++]=pop();

push(x);

}

while (top>=0)

postfix[n++]=pop();

}

int main()

{

init();

clrscr();

printf("\n Conversion of Infix to Postfix expression Using Stack\n");

printf("\nEnter an infix expression :\t");

scanf("%s",infix);

infixtopostfix();

printf("\nThe resulting postfix expression is : \t%s",postfix);

getch();

return 0;

}

```
