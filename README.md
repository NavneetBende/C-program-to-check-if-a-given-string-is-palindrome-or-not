Check whether a String is Palindrome in C
Today in this article we will learn how to Check whether a String is Palindrome using C Programming language.

A string is palindrome if the reverse and the original string is same

Lets understand this with the help of an example:- 

Input sting:- AMA
Reverse sting:- AMA
Here AMA = AMA so this is a palindrome 

Check whether a String is Palindrome
Methods Discussed
Method 1: Simple iterative
Method 2: Iterative with a shorter loop
Method 3: Binary Search inspiration
Method 1
To check String is palindrome or not in C

For a String of Length: Len
Run an iterative loop in an iteration of i
If encounter any index such that arr[i] != arr[len – i -1], then the string is not palindrome
Otherwise if no condition such found in whole iteration in loop then string is palindrome
Check whether a String is Palindrome
Method 1 Code
Run
#include <stdio.h>
#include <string.h>


int main() 
{
    char str[10] = "naman";
    int i, len, flag = 0;
    
    len = strlen(str);

    for (i = 0; i < len; i++) 
    {
        // Checking if string is palindrome or not
        if (str[i] != str[len - i - 1]) {
            flag = 1;
            break;
        }
    }

    if (flag)
        printf("%s is not palindrome", str);
    else
        printf("%s is palindrome", str);
        
    return 0;
}
Output
naman is palindrome
While loop in C
Related Pages
Juggling algorithm for array rotation
 
Balanced Parenthesis Problem
 
Toggle each character in a string

Count the number of vowels

Length of the string without using strlen() function

Method 2
This method is the same as the above method with two minor differences –

Difference 1
For loop runs only till len/2 not the whole length of the string
Since the other half, the string will be the same as the first half. If the string is a palindrome
Difference 2
We also handle capitalization
The previous method would have said “Naman” is not palindrome as N is not equal to n
This method converts the whole string into lowercase and thus will say that “Naman” is palindrome
Run
#include <stdio.h>
#include <string.h>

void lowerCase(char str[]){
  int i = 0;
  while (str[i] != '\0')
  {
    if (str[i] > 64 && str[i] < 91) 
      str[i] += 32; 
    i++;
  }
}
int main() 
{
    char str[10] = "Naman";
    int i, len, flag = 0;
    
    lowerCase(str);
    
    len = strlen(str);
    
    // only need to check till half of the array
    for (i = 0; i < len / 2; i++) 
    {
        // Checking if string is palindrome or not.
        if (str[i] != str[len - i - 1]){
            flag++;
            break;
        }
    }

    if (flag)
        printf("String is not palindrome");
    else
        printf("String is palindrome");
        
    return 0;
}
Output
String is palindrome
Method 3
This method is the same as the above method. However, instead of for loop, we use a whole loop.

The approach is very similar to Binary search looping

Run

#include <stdio.h>
#include <string.h>


void Lower_case(char str[]) {
    int i = 0;
    while (str[i] != '\0') {
        if (str[i] > 64 && str[i] < 91) 
            str[i] += 32; 

        i++; 
    } 
} 

void CheckPalindrome(char str[]) 
{ 

    // to mark left most and right most indexes of string 
    int left = 0; 
    int right = strlen(str) - 1; 

    // Keep comparing characters while they are same 
    // until left and right overlap one another 
    // inspiration for this approach taken from binary search 
    while (right > left) 
    {
        if (str[left++] != str[right--]) {
            printf("The String %s is not a palindrome", str);
            return;
        }
    }
    printf("The String %s is palindrome", str);
}
int main() 
{
    char str1[50] = "Radar";
    
    Lower_case(str1);
    CheckPalindrome(str1);
    
    return 0;
}
Output
The String radar is palindrome
