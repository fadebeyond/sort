// C++ program for implementation of selection sort 
#include <bits/stdc++.h>
using namespace std;
void swap(int *xp, int *yp) 
{ 
int temp = *xp; 
*xp = *yp; 
*yp = temp; 
} 
void selectionSort(int arr[], int n) 
{ 
int i, j, min_idx; 
// One by one move boundary of unsorted subarray 
for (i = 0; i < n-1; i++) 
{ 
// Find the minimum element in unsorted array 
min_idx = i; 
for (j = i+1; j < n; j++) 
if (arr[j] < arr[min_idx]) 
min_idx = j; 
// Swap the found minimum element with the first element 
swap(&arr[min_idx], &arr[i]); 
} 
} 
/* Function to print an array */
void printArray(int arr[], int size) 
{ 
int i; 
for (i=0; i < size; i++) 
cout << arr[i] << " "; 
cout << endl; 
} 
// Driver program to test above functions 
int main() 
{ 
int arr[] = {64, 25, 12, 22, 11}; 
int n = sizeof(arr)/sizeof(arr[0]); 
selectionSort(arr, n); 
cout << "Sorted array: \n"; 
printArray(arr, n); 
return 0; 


// C++ program for implementation of Bubble sort
#include <bits/stdc++.h>
using namespace std;
void swap(int *xp, int *yp)
{
int temp = *xp;
*xp = *yp;
*yp = temp;
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
/* Function to print an array */
void printArray(int arr[], int size)
{
int i;
for (i = 0; i < size; i++)
cout << arr[i] << " ";
cout << endl;
}
// Driver code
int main()
{
int arr[] = {64, 34, 25, 12, 22, 11, 90};
int n = sizeof(arr)/sizeof(arr[0]);
bubbleSort(arr, n);
cout<<"Sorted array: \n";
printArray(arr, n);
return 0;
}


// C++ program for insertion sort
#include <bits/stdc++.h>
using namespace std;
/* Function to sort an array using insertion sort*/
void insertionSort(int arr[], int n)
{
int i, key, j;
for (i = 1; i < n; i++)
{
key = arr[i];
j = i - 1;
/* Move elements of arr[0..i-1], that are
greater than key, to one position ahead
of their current position */
while (j >= 0 && arr[j] > key)
{
arr[j + 1] = arr[j];
j = j - 1;
}
arr[j + 1] = key;
}
}
// A utility function to print an array of size n
void printArray(int arr[], int n)
{
int i;
for (i = 0; i < n; i++)
cout << arr[i] << " ";
cout << endl;
}
/* Driver code */
int main()
{
int arr[] = { 12, 11, 13, 5, 6 };
int n = sizeof(arr) / sizeof(arr[0]);
insertionSort(arr, n);
printArray(arr, n);
return 0;
}



// C++ program for Merge Sort

#include <iostream>

using namespace std;
// Merges two subarrays of array[].
// First subarray is arr[begin..mid]
// Second subarray is arr[mid+1..end]
void merge(int array[], int const left, int const mid, int const right)
{
auto const subArrayOne = mid - left + 1;
auto const subArrayTwo = right - mid;
// Create temp arrays
auto *leftArray = new int[subArrayOne],
*rightArray = new int[subArrayTwo];
// Copy data to temp arrays leftArray[] and rightArray[]
for (auto i = 0; i < subArrayOne; i++)
leftArray[i] = array[left + i];
for (auto j = 0; j < subArrayTwo; j++)
rightArray[j] = array[mid + 1 + j];
auto indexOfSubArrayOne = 0, // Initial index of first sub-array
indexOfSubArrayTwo = 0; // Initial index of second sub-array
int indexOfMergedArray = left; // Initial index of merged array
// Merge the temp arrays back into array[left..right]
while (indexOfSubArrayOne < subArrayOne && indexOfSubArrayTwo < 
subArrayTwo) {
if (leftArray[indexOfSubArrayOne] <= rightArray[indexOfSubArrayTwo]) {
array[indexOfMergedArray] = leftArray[indexOfSubArrayOne];
indexOfSubArrayOne++;
}
else {
array[indexOfMergedArray] = rightArray[indexOfSubArrayTwo];
indexOfSubArrayTwo++;
}
indexOfMergedArray++;
}
// Copy the remaining elements of
// left[], if there are any
while (indexOfSubArrayOne < subArrayOne) {
array[indexOfMergedArray] = leftArray[indexOfSubArrayOne];
indexOfSubArrayOne++;
indexOfMergedArray++;
}
// Copy the remaining elements of
// right[], if there are any

while (indexOfSubArrayTwo < subArrayTwo) {
array[indexOfMergedArray] = rightArray[indexOfSubArrayTwo];
indexOfSubArrayTwo++;
indexOfMergedArray++;
}
}
// begin is for left index and end is
// right index of the sub-array
// of arr to be sorted */
void mergeSort(int array[], int const begin, int const end)
{
if (begin >= end)
return; // Returns recursively
auto mid = begin + (end - begin) / 2;
mergeSort(array, begin, mid);
mergeSort(array, mid + 1, end);
merge(array, begin, mid, end);
}
// UTILITY FUNCTIONS
// Function to print an array
void printArray(int A[], int size)
{
for (auto i = 0; i < size; i++)
cout << A[i] << " ";
}
// Driver code
int main()
{
int arr[] = { 12, 11, 13, 5, 6, 7 };
auto arr_size = sizeof(arr) / sizeof(arr[0]);
cout << "Given array is \n";
printArray(arr, arr_size);
mergeSort(arr, 0, arr_size - 1);
cout << "\nSorted array is \n";
printArray(arr, arr_size);
return 0;
}


//* C++ implementation of QuickSort */
#include <bits/stdc++.h>
using namespace std;
// A utility function to swap two elements
void swap(int* a, int* b)
{
int t = *a;
*a = *b;
*b = t;
}
/* This function takes last element as pivot, places
the pivot element at its correct position in sorted
array, and places all smaller (smaller than pivot)
to left of pivot and all greater elements to right
of pivot */
int partition (int arr[], int low, int high)
{
int pivot = arr[high]; // pivot
int i = (low - 1); // Index of smaller element and indicates the right 
position of pivot found so far
for (int j = low; j <= high - 1; j++)
{
// If current element is smaller than the pivot
if (arr[j] < pivot)
{
i++; // increment index of smaller element
swap(&arr[i], &arr[j]);
}
}
swap(&arr[i + 1], &arr[high]);
return (i + 1);
}
/* The main function that implements QuickSort
arr[] --> Array to be sorted,
low --> Starting index,
high --> Ending index */
void quickSort(int arr[], int low, int high)
{
if (low < high)
{
/* pi is partitioning index, arr[p] is now
at right place */
int pi = partition(arr, low, high);
// Separately sort elements before
// partition and after partition
quickSort(arr, low, pi - 1);
quickSort(arr, pi + 1, high);
}
}
/* Function to print an array */
void printArray(int arr[], int size)
{
int i;
for (i = 0; i < size; i++)
cout << arr[i] << " ";
cout << endl;
}
// Driver Code
int main()
{
int arr[] = {10, 7, 8, 9, 1, 5};
int n = sizeof(arr) / sizeof(arr[0]);
quickSort(arr, 0, n - 1);
cout << "Sorted array: \n";
printArray(arr, n);
return 0;
}


// C++ implementation of Radix Sort
#include <iostream>
using namespace std;
// A utility function to get maximum value in arr[]
int getMax(int arr[], int n)
{
int mx = arr[0];
for (int i = 1; i < n; i++)
if (arr[i] > mx)
mx = arr[i];
return mx;
}
// A function to do counting sort of arr[] according to
// the digit represented by exp.
void countSort(int arr[], int n, int exp)
{
int output[n]; // output array
int i, count[10] = { 0 };
// Store count of occurrences in count[]
for (i = 0; i < n; i++)
count[(arr[i] / exp) % 10]++;
// Change count[i] so that count[i] now contains actual
// position of this digit in output[]
for (i = 1; i < 10; i++)
count[i] += count[i - 1];
// Build the output array
for (i = n - 1; i >= 0; i--) {
output[count[(arr[i] / exp) % 10] - 1] = arr[i];
count[(arr[i] / exp) % 10]--;
}
// Copy the output array to arr[], so that arr[] now
// contains sorted numbers according to current digit
for (i = 0; i < n; i++)
arr[i] = output[i];
}
// The main function to that sorts arr[] of size n using
// Radix Sort
void radixsort(int arr[], int n)
{
// Find the maximum number to know number of digits
int m = getMax(arr, n);
// Do counting sort for every digit. Note that instead
// of passing digit number, exp is passed. exp is 10^i
// where i is current digit number
for (int exp = 1; m / exp > 0; exp *= 10)
countSort(arr, n, exp);
}
// A utility function to print an array
void print(int arr[], int n)
{
for (int i = 0; i < n; i++)
cout << arr[i] << " ";
}
// Driver Code
int main()
{
int arr[] = { 170, 45, 75, 90, 802, 24, 2, 66 };
int n = sizeof(arr) / sizeof(arr[0]);
// Function Call
radixsort(arr, n);
print(arr, n);
return 0;
}




// C++ palindrome check in stack

#include <bits/stdc++.h>

using namespace std;
// Function that returns true
// if string is a palindrome
bool isPalindrome(string s)
{
int length = s.size();
// Creating a Stack
stack<char> st;
// Finding the mid
int i, mid = length / 2;
for (i = 0; i < mid; i++) {
st.push(s[i]);
}
// Checking if the length of the string
// is odd, if odd then neglect the
// middle character
if (length % 2 != 0) {
i++;
}
char ele;
// While not the end of the string
while (s[i] != '\0')
{
ele = st.top();
st.pop();
// If the characters differ then the
// given string is not a palindrome
if (ele != s[i])
return false;
i++;
}
return true;
}
// Driver code
int main()
{
string s = "madam";
if (isPalindrome(s)) {
cout << "Yes";
}
else {
cout << "No";
}
return 0;
}

// reverses the given stack using
// insert_at_bottom()
void reverse()
{
if(st.size()>0)
{
// Hold all items in Function
// Call Stack until we
// reach end of the stack
char x = st.top();
st.pop();
reverse();
// Insert all the items held
// in Function Call Stack
// one by one from the bottom
// to top. Every item is
// inserted at the bottom
insert_at_bottom(x);
}
}
// Driver Code
int main()
{
// push elements into
// the stack
st.push('1');
st.push('2');
st.push('3');
st.push('4');
cout<<"Original Stack"<<endl;
// print the elements
// of original stack
cout<<"1"<<" "<<"2"<<" "
<<"3"<<" "<<"4"
<<endl;
// function to reverse
// the stack
reverse();
cout<<"Reversed Stack"
<<endl;

while(!st.empty())
{
char p=st.top();
st.pop();
ns+=p;
}
//display of reversed stack
cout<<ns[3]<<" "<<ns[2]<<" "
<<ns[1]<<" "<<ns[0]<<endl;
return 0;
}

#include <bits/stdc++.h>
using namespace std;
#define MAX 1000
class Stack {
int top;
public:
int a[MAX]; // Maximum size of Stack
Stack() { top = -1; }
bool push(int x);
int pop();
int peek();
bool isEmpty();
};
bool Stack::push(int x)
{
if (top >= (MAX - 1)) {
cout << "Stack Overflow";
return false;
}
else {
a[++top] = x;
cout << x << " pushed into stack\n";
return true;
}
}
int Stack::pop()
{
if (top < 0) {
cout << "Stack Underflow";
return 0;
}
else {
int x = a[top--];
return x;
}
}
int Stack::peek()
{
if (top < 0) {cout << "Stack is Empty";
return 0;

}
else {
int x = a[top];
return x;
}
}
bool Stack::isEmpty()
{
return (top < 0);
}
// Driver program to test above functions
int main()
{
class Stack s;
s.push(10);
s.push(20);
s.push(30);
cout << s.pop() << " Popped from stack\n";
//print all elements in stack :
cout<<"Elements present in stack : ";
while(!s.isEmpty())
{
// print top element in stack
cout<<s.peek()<<" ";
// remove top element in stack
s.pop();
}
return 0;
}
