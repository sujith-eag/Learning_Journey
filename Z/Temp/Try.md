Decode String - Given an encoded string where repetition of substrings are indicated by a number followed by square brackets (e.g `3[abc]`), decode the string using a stack.
`3[abc]` should decode as `abcabcabc`


Take input as string of characters.

Take the first character as number, convert it to digit, 
( edge case if number is 2 or 3 digits long, iterate till `[` is reached , have a method to convert to a number )

Using stack in array implementation,
	Take the number from the code and pass it to a for loop,
	push the string into the stack for the given number of times
	Once the loop is over, reverse with calling pop the same number of times and `printf` without line break till end of loop.
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

void main()
{
	char string[100];
	printf("Enter the Encoded String in the format 3[abcd] : \n");
	
	scanf("%s", string);
	int count = parse_number(string);
	printf("\nThere are %i Repetetions\n", count);

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
			}
			j--;
		}
		
	}
	printf("\nThe Sequence Will be :\t");

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