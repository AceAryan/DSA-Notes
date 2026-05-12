## Paranthesis Matching
check if every paranthesis is completed i.e. for every **(** there is a **)** to complete it

push **(** into the stack
pop **(** everytime you encounter a **)** from the stack
paranthesization is **balanced** if at the end of program stack is *empty*

```cpp
struct stack {
	int size;
	int top;
	char *s;
}
```

```cpp
int isBalance (char *exp){
	struct stack st;
	st.size = strlen(exp);
	st.top = -1;
	st.s = new char[st.size];
	
	for(int i=0; exp[i]! = '\0'; i++){
		if (exp[i]=='(') 
			push (&st, exp[i]);
		else if (exp[i]==')'){
			if (isEmpty(st)) return false;
			pop(&st);
		}
	}
	return isEmpty(st) ? true : false;
}
```

###### with different types of brackets
( , [ , {

```cpp
int isBalance (char *exp){
	struct stack st;
	st.size = strlen(exp);
	st.top = -1;
	st.s = new char[st.size];
	
	for(int i=0; exp[i]! = '\0'; i++){
		if (exp[i]=='(' || exp[i]=='[' || exp[i]=='{') 
			push (&st, exp[i]);
		else if (exp[i]==')' || exp[i]==']' || exp[i]=='}') {
		 if (isEmpty(st)){
			 delete[] st.s; 
			 return false; 
		}
		 
		char topChar = st.s[st.top];
 		if ((exp[i] == ')' && topChar == '(') || (exp[i] ==           ']' && topChar == '[') || (exp[i] == '}' && topChar           == '{')) {
	 		pop(&st); 
 		}
 		else { 
	 		delete[] st.s;
	 		return false;
 		}
 	}
	return isEmpty(st) ? true : false;
}
```

## Infix to Postfix Conversion

1. **Infix** : operand operator operand *( $a + b$ )*
2. **Prefix** : opt opnd opnd *( $+ a b$ )*
3. **Postfix** : opnd opnd opt *( $a b +$ )*

postfix helps to evaluate expressions using **BODMAS** by scanning only once

| **symbol** | *precedence* |
| ---------- | ------------ |
| + -        | 1            |
| * /        | 2            |
| ( )        | 3            |
always convert the expression to **fully paranthesized**
same precedence -> go **Left to Right**

eg.
$a + b * c = ( a + (b*c))$
*postfix exprn* : $(a+(bc*))$ = $abc*+$

#### Associativity and Unary Operators

| **symbol** | *precedence* | *associativity* |
| ---------- | ------------ | --------------- |
| + -        | 1            | L - R           |
| * /        | 2            | L - R           |
| ^          | 3            | R - L           |
| *-*        | 4            | R - L           |
| ( )        | 5            | L - R           |

eg. *unary negation* : $--a$ , *postfix* : $a--$

eg.
$-a+b*log n!$ = $-a+b*log (n!)$ = $-a+b*(n!log)$ = $(a-)+b*(n!log)$ = $(a-)+(bn!log*)$ = $a-bn!log*+$

##### Infix to Postfix using Stack
push if operator precedence > precedence of top element in stack
otherwise pop

```cpp
int isOperand(char x){
	if(x=='+' || x=='-' || x=='*' || x=='/')
		return 0;
	else
		return 1;
}
```

```cpp
int pre(char x){
	if(x=='+'||x=='-')
		return 1;
	else if(x=='*'||x=='/')
		return 2;
	return 0;
}
```

```cpp
char *convert (char *infix){
	struct stack st; //Initialization
	st.size = strlen(exp);
	st.top = -1;
	st.s = new char[st.size];
	char *postfix = new char[strlen(infix)+1];
	int i=0; j=0;
	while (infix[i]!='\0'){
		if(isOperand(infix[i]))
			postfix[j++] = infix[i++];
		else{
			if(pre(infix[i])>pre(stackTop(st)))
				push(&st,infix[i++]);
			else
				postfix[j++] = pop(&st);
		}
	}
	// for loop cant be used because we are not incrementing         i everytime
	while (!isEmpty(st)){
		postfix[j++] = pop(&st);
	}
	postfix[j]='\0';
	return postfix;
}
```

##### Evaluation of Postfix
push operands into stack, upon encountering operator, pop 2 elements form stack, perform that operation and again push into stack. at end of expression, result is inside stack.

```cpp
int Eval (char *postfix){
	struct stack st;
	int i, x1, x2, r;
	for (int i=0; postfix[i]!='\0'; i++){
		if (isOperand(postfix[i]))
			push (&st, postfix[i] - '0'); //converting char                                from string to int for operation
		else {
			x2 = pop(&st); x1 = pop(&st);
			switch(postfix[i]){
				case '+': r=x1+x2; push(&st,r); break;
				case '-': r=x1-x2; push(&st,r); break;
				case '*': r=x1*x2; push(&st,r); break;
				case '/': r=x1/x2; push(&st,r); break;
			} 
		}
	}
	return pop(&st);
}
```

**precedence and associativity are for paranthesization not execution**
