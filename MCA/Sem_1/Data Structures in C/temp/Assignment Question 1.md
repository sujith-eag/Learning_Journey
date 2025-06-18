Decode String - Given an encoded string where repetition of substrings are indicated by a number followed by square brackets (e.g `3[abc]`), decode the string using a stack.
`3[abc]` should decode as `abcabcabc`

___


Take input as string of characters.
Using stack in array implementation,
Take the first character as number, convert it to digit (will miss double digits) .
For handling multiple numbers, iterate till `[` is reached, each iteration accumulates number by converting to a number. Returned at end of iteration as the given number.

Take the number and pass it to a for loop to iterate that many times.
Using while loop Push each character into the stack from end to the beginning brace `[`, discarding the `]`.

After loop ends, call pop till stack is empty, `printf` without line break till end of loop.


```c
#include <stdio.h>

char stack[100];
int Top = -1;

int length(char *string);
int parse_number(char *string);
void push(char x);
char pop();

void main()
{
	char string[100];
	printf("Enter the Encoded String in the format 3[abcd] : \n");
	
	scanf("%s", string);
		// getting the number part
	while(string[0] != 'q')
	{	
		int count = parse_number(string);
		printf("\nThere are %i Repetetions\n", count);
			// Iterate for the given count number
		for( int i = count ; i>0 ; i--)
		{         // push characters in reverse order till opening brace
			int j = length(string);
			while(string[j] != '[')
			{
				if( string[j] == ']')
					;
				else 
				{
					push(string[j]);
				}
				j--;
			}
		}
		printf("The Sequence Will be :\t");
	
		while(Top != -1)
		{      // pop all will no elements in stack
			printf("%c", pop());
		}
		printf("\n\n");

		printf("Enter String in format 3[abcd] or Enter q to Exit: \n");
		scanf("%s", string);
	}
}

int parse_number(char *string)
{
	int len = 0;
	int total=0, temp =0;
	while(string[len] != '[')
	{
		temp = string[len]-48;
		total = total*10 + temp;
		len++;
	}
	return total;
}
int length(char *string)
{
	int i = 0;
	while( string[i] != '\0')
	{
		i++;
	}
	return i;
}
void push(char x)
{
	Top++;
	stack[Top] = x;
}
char pop()
{
	return(stack[Top--]);
}
```

```c
// Not necessary to find num length as i was iterating forward

int parse_number(char *string)
{
	int num_len = 0;
	while(string[num_len] != '[')
	{
		num_len++;
	}
	
	int total=0, temp =0;
	
	for( int i = 0 ; i < num_len ; i++)
	{
		temp = string[i]-48;
		total = total*10 + temp;
	}
	return total;
}
```

```c
#include <stdio.h>

char stack[100];
int Top = -1;

void push(char x)
{
	Top++;
	stack[Top] = x;
}
char pop()
{
	return(stack[Top--]);

}
int length(char *string)
{
	int i = 0;
	while( string[i] != '\0')
	{
		i++;
	}
	return i;
}

void main()
{
	char string[100];
	printf("Enter the Encoded String in the format 3[abcd] : \n");
	
	scanf("%s", string);
	int count = string[0]-48;
	printf("%i", count);

	for( int i = count ; i>0 ; i--)
	{
		int j = length(string);
		while(string[j] != '[')
		{
			if( string[j] == ']')
				;
			else 
			{
				push(string[j]);
				printf("%c", string[j]);
			}
			j--;
		}
		
	}
	printf("\nThe Sequence Will be :\n");

	while(Top != -1)
	{
		printf("%c", pop());
	}
	printf("\n");
}
```

```c
#include <stdio.h>

char stack[100];
int Top = -1;

void push(char x)
{
	Top++;
	stack[Top] = x;
}
char pop()
{
	return(stack[Top--]);

}
int length(char *string)
{
	int i = 0;
	while( string[i] != '\0')
	{
		i++;
	}
	return i;
}
int parse_number(char *string)
{    

	int num_len = 0;
	while( string[num_len] != '[' )
	{
		num_len++;
	}

	int temp, total=NULL;
	for( int i = num_len; i>0 ; i--)
	{
		if(i == 3)
		{
			//if( string[i] == '0') ;
			//else
			temp = string[i--]-48;
			total += temp*100;
			temp=string[i--]-48;
			total += temp*10;
			temp=string[i--]-48;
			total += temp;
			return total;
		}
		if(i == 2)
		{
			temp=string[i--]-48;
			total += temp*10;
			temp=string[i--]-48;
			total += temp;
			return total;
		}
		if(i==1)
			return string[i]-48;
	}
}
void main()
{
	char string[100];
	printf("Enter the Encoded String in the format 3[abcd] : \n");
	
	scanf("%s", string);
	int count = parse_number(string);
	printf("%i", count);

	for( int i = count ; i>0 ; i--)
	{
		int j = length(string);
		while(string[j] != '[')
		{
			if( string[j] == ']')
				;
			else 
			{
				push(string[j]);
				printf("%c", string[j]);
			}
			j--;
		}
		
	}
	printf("\nThe Sequence Will be :\n");

	while(Top != -1)
	{
		printf("%c", pop());
	}
	printf("\n");
}
```