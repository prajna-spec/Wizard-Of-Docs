# ⭐ BUBBLE SORT

Bubble Sort is the simplest and most classical sorting algorithm that works by comparing and swapping the adjacent elements if they are in wrong order. While this may not be the most efficient sorting way, it is certainly easiest to understand and implement.

#### Example: 

##### Input: [5 1 4 2 8]

##### First Pass: 
( 5 1 4 2 8 ) –> ( 1 5 4 2 8 ), Here, algorithm compares the first two elements, and swaps since 5 > 1. 
( 1 5 4 2 8 ) –>  ( 1 4 5 2 8 ), Swap since 5 > 4 
( 1 4 5 2 8 ) –>  ( 1 4 2 5 8 ), Swap since 5 > 2 
( 1 4 2 5 8 ) –> ( 1 4 2 5 8 ), Now, since these elements are already in order (8 > 5), algorithm does not swap them.

##### Second Pass: 
( 1 4 2 5 8 ) –> ( 1 4 2 5 8 ) 
( 1 4 2 5 8 ) –> ( 1 2 4 5 8 ), Swap since 4 > 2 
( 1 2 4 5 8 ) –> ( 1 2 4 5 8 ) 
( 1 2 4 5 8 ) –>  ( 1 2 4 5 8 ) 
Now, the array is already sorted, but our algorithm does not know if it is completed. The algorithm needs one whole pass without any swap to know it is sorted.

##### Third Pass: 
( 1 2 4 5 8 ) –> ( 1 2 4 5 8 ) 
( 1 2 4 5 8 ) –> ( 1 2 4 5 8 ) 
( 1 2 4 5 8 ) –> ( 1 2 4 5 8 ) 
( 1 2 4 5 8 ) –> ( 1 2 4 5 8 ) 

##### Output: [1 2 4 5 8]

Now, generally we would resort to the above method of implementing bubble sort. Since we are iterating through the array N number of times (N is the numbr of elements in the input array), the time complexity would be O(N^2). We are not using any additional space, so the space complexity would be O(1).

However, if we can somehow inform our algorithm that the array is already sorted, then we wont have to traverse the remaining passes. To do this we can use a flag. Two solutions implementing this approach will be given below. This wont change the worst time complexity but the best time complexity would improve to O(N).

### SOLUTION 1
```
def bubbleSort(array):
    # Write your code here.
    for i in range(len(array)):
    // This check is to ensure that the array is not already sorted before going through another pass.
		alreadySorted = True
		for j in range(len(array) - i - 1):
			if array[j] > array[j+1]:
        // Setting alreadySorted to false when the condition is true.
				alreadySorted = False
				array[j], array[j+1] = array[j+1], array[j]
		if alreadySorted:
			break
			
	return array
```

### SOLUTION 2. A variation to the above solution using while loop.
```
def bubbleSort(array):
    # Write your code here.
    alreadySorted = False
	i = 0
  // This check is to ensure that the array is not already sorted before going through another pass.
	while not alreadySorted:
		alreadySorted = True
		for j in range(len(array) - i - 1):
			if array[j] > array[j+1]:
				alreadySorted = False
				array[j], array[j+1] = array[j+1], array[j]
		i += 1
		
	return array
	
```
### SOLUTION 2. BUBBLESORT in cpp
```
// C++ program for implementation of Bubble sort
#include <bits/stdc++.h>
using namespace std;

//this function can swap two numbers
 
void swap(int *x,int *y)
{
    int temp = *x;
    *x = *y;
    *y = temp;
}
 
// A function to implement bubble sort
void bubbleSort(int arr[], int n)
{
    int i, j;
    for (i = 0; i < n-1; i++)    
     
    // Last i elements are already in place
    for (j = 0; j < n-i-1; j++)
        if (arr[j] > arr[j+1])
            swap(&arr[j], &arr[j+1]);
}
 
//function to print the array
void Array_print(int arr[], int n)
{
    int i;
    for (i = 0; i < size; i++)
        cout << arr[i] << " ";
    cout << endl;
}
 
// Driver code
int main()
{
    
    int n;
    cout<<"Enter the size of the array"<<endl;
    cin>>n;
    int arr[n];
    for(int i=0;i<n;i++)
    {
      cin>>arr[i];
    }
    bubbleSort(arr, n);
    cout<<"Sorted array: \n";
    Array_print(arr, n);
    return 0;
}
```


### SOLUTION 2 in cpp: SPACE OPTIMISED APPROACH:

```
This approach is further optimised.
Here we observe that if the array is not swapped we can stop it from performing further passes by setting the flag flag variable to false

#include <bits/stdc++.h>
using namespace std;
void swap(int *x, int *y)
{
    int temp = *x;
    *x = *y;
    *y = temp;
}
 

void bubbleSort(int arr[], int n)
{
   bool flag;
   int i, j;
 
   for (i = 0; i < n-1; i++)
   {
     flag = 0;
     for (j = 0; j < n-i-1; j++)
     {
        if (arr[j] > arr[j+1])
        {
           swap(&arr[j], &arr[j+1]);
           flag = 1;
        }
     }
 
    
     if (flag==0)
        break;
   }
}
 
/* Function to print an array */
void Array_print(int arr[], int size)
{
   
    for (int i = 0; i < size; i++)
        cout <<" "<< arr[i]<<" ";
    
}
int main()
{
     
    int n;
    cout<<"Enter the size of the array"<<endl;
    cin>>n;
    int arr[n];
    cout<<"Enter the values"<<endl;
    for(int i=0;i<n;i++)
    {
      cin>>arr[i];
    }
    bubbleSort(arr, n);
    cout<<"Sorted array:";
    Array_print(arr, n);
    return 0;
}
```

#### ⏲️ Time Complexities:
Best: O(N)
<br/>
Average: O(N^2)
<br/>
Worst: O(N^2)

#### 👾 Space complexities:
Best: O(1)
<br/>
Average: O(1)
<br/>
Worst: O(1)
