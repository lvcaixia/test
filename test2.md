#include <iostream>

 

using namespace std;

 

intarrayMaxSum(int* arr, int n)

{

int sum = arr[0];

inttmp = 0;

 

for(inti=0; i<n; i++)

    {

if(tmp< 0)

tmp = arr[i];

else

tmp += arr[i];

if (sum <tmp)

sum = tmp;

 

    }

return sum;

}

 

int main()

{

intmyArr[100] = {1, -2, 3, 5, -1};

intnum = 5;

intrlt = arrayMaxSum(myArr, num);

cout<<rlt;

return 0;

}
