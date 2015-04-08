#include <iostream>

#include <cstring>

 

using namespace std;

 

voidswapChar(char &a, char &b)

{

chartmp = b;

    b = a;

    a = tmp;

}

 

voidsentenceSwap(char* str, intsBegin, intsEnd)

{

int low = sBegin;

int high = sEnd;

 

while (low < high)

    {

swapChar(str[low], str[high]);

low++;

high--;

    }

}

 

voidreverseWord(char str[])

{

intlen = strlen(str);

 

sentenceSwap(str, 0, len-1);

 

int s = 0;

int e = 0;

 

for (inti=0; i<len; i++)

    {

        e = i;

if (str[e] == ' ')

        {

sentenceSwap(str, s, e-1);

            s = e + 1;

        }

if (e == len-1)

        {

sentenceSwap(str, s, e);

        }

    }

}

 

int main()

{

charstr[] = "hosw are you";

reverseWord(str);

cout<<str<<endl;

return 0;

}

 
