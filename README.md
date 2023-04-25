
# Binary Search

Binary search is an algorithm for finding the position of a target value within a sorted array. It works by repeatedly dividing the search interval in half until the target value is found or the search interval is empty. Binary search requires the array to be sorted in order for it to work correctly. If the array is not sorted, binary search will not find the target value correctly.

![binary-search2](https://user-images.githubusercontent.com/88421625/234429731-270c8ccd-8de9-4864-b614-faf9a8d8feee.jpg)

Here is an implementation of binary search in C:
```bash
#include <stdio.h>

int binary_search(int arr[], int n, int x) {
    int low = 0, high = n - 1, mid;
    
    while (low <= high) {
        mid = (low + high) / 2;
        if (arr[mid] == x) {
            return mid;
        } else if (arr[mid] < x) {
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }
    
    return -1; // element not found
}

int main() {
    int arr[] = {2, 4, 6, 8, 10, 12, 14, 16};
    int n = sizeof(arr) / sizeof(arr[0]);
    int x = 10;
    
    int index = binary_search(arr, n, x);
    if (index == -1) {
        printf("Element not found\n");
    } else {
        printf("Element found at index %d\n", index);
    }
    
    return 0;
}
```
In this implementation, ‘binary_search’ takes an array ‘arr’, its size n, and the element to be searched for ‘x’ as input. It uses two indices, ‘low’ and ‘high’, to keep track of the range of the array where ‘x‘ might be found.

The function starts by initializing ‘low’ to 0 and ‘high’ to ‘n – 1’. It then enters a loop that continues as long as ‘low’ is less than or equal to ‘high’. In each iteration of the loop, the function computes the midpoint of the current range using the formula ‘(low + high) / 2’.

If the element at the midpoint is equal to x, the function returns the index of the midpoint. If the element at the midpoint is less than ‘x’, the function updates ‘low’ to ‘mid + 1’, effectively discarding the lower half of the current range. If the element at the midpoint is greater than x, the function updates ‘high’ to ‘mid – 1’, effectively discarding the upper half of the current range.

If the loop completes without finding the element ‘x’, the function returns -1 to indicate that the element was not found.

In the main function, we define an array ‘arr’, its size ‘n’, and the element to be searched for ‘x’. We then call ‘binary_search’ with these parameters and store the result in the variable index. If ‘index’ is -1, we print a message indicating that the element was not found. Otherwise, we print a message indicating the index where the element was found.


## Key Points
Here are some important points about Binary Search:

•	Binary search is a divide-and-conquer algorithm that can be used to search for a specific element in a sorted array.

•	The algorithm works by repeatedly dividing the array into halves until the element is found or the search range is reduced to an empty array.

•	In order to use binary search, the array must be sorted in ascending or descending order.

•	The basic implementation of binary search involves keeping track of two indices, ‘low’ and ‘high’, that define the current range of the array being searched.

•	The algorithm computes the midpoint of the range using the formula ‘(low + high) / 2’ and compares the element at that index with the search key.

•	If the element at the midpoint is equal to the search key, the algorithm returns the index of the midpoint.

•	If the element at the midpoint is less than the search key, the algorithm updates ‘low’ to ‘mid + 1’, effectively discarding the lower half of the range.

•	If the element at the midpoint is greater than the search key, the algorithm updates ‘high’ to ‘mid – 1’, effectively discarding the upper half of the range.

•	The algorithm continues to divide the remaining range in half until either the element is found or the range is reduced to an empty array.

•	If the element is not found, the algorithm returns -1 to indicate that the element was not present in the array.

•	Binary search has a time complexity of O(log n), which is much faster than linear search for large arrays.

•	It is important to ensure that the array is sorted and that the search range is valid (i.e., ‘low’ is less than or equal to ‘high’) in order to avoid errors in the implementation.



# Code

```bash
// implementing binary search

#include <stdio.h>

void Bubble(int a[], int n);
int Binary(int a[], int element, int n);

int main()
{
    int arr[5] = {2, 107, 81, 5, 24};

    int key;

    printf("Enter an element: ");
    scanf("%d", &key);

    // calling the sort and search functions
    Bubble(arr, 5);
    int result = Binary(arr, key, 5);

    if(result == 1)
    {
        printf("Element found.\n");
    }
    else
    {
        printf("Element not found.\n");
    }
    

    return 0;
}


// bubble sort (ascending order)
void Bubble(int a[], int n)
{
    // no. of passes (p) and no. of comparisons for each pass
    int p = n - 1;
    int c = n - 1;

    int i, j;

    for(i = 0; i < p; i++)
    {
        for(j = 0; j < c - i; j++)
        {
            // swapping the adjacent elements if the first is larger than the second 
            if(a[j] > a[j + 1])
            {
                int temp = a[j];
                a[j] = a[j + 1];
                a[j + 1] = temp;
            }

        }
    }
}


// binary search
int Binary(int a[], int element, int n)
{
    int lower = 0;
    int upper = n;

    int mid;

    while(lower <= upper)
    {
        // finding the middle element of the passed array
        mid = (lower + upper) / 2;

        if(element == a[mid])
        {
            return 1;
        }
        else if(element > a[mid])
        {
            lower = mid + 1;
        }
        else
        {
            upper = mid - 1;
        }

    }

    return -1;
}
```
## Output
![OP1](https://user-images.githubusercontent.com/88421625/234429397-c3847b43-b0b0-47c9-ab5b-36cf816cbc80.png)

![OP2](https://user-images.githubusercontent.com/88421625/234429400-f015b0af-795f-41c8-a87c-f4edd516ad93.png)

![OP3](https://user-images.githubusercontent.com/88421625/234429402-cf49d62f-7f98-45d6-9ed7-c20181678dac.png)

![OP4](https://user-images.githubusercontent.com/88421625/234429406-0f0edc99-4ffe-478b-8fba-51e4f023b753.png)
