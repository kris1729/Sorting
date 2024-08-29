# Selection Sort
Chose mini ans put at the first place , than schose other mini and put it second place

```cpp
void selectionSort(int arr[], int n){
    
    for(int i =0;i<n-1;i++)
    {
        int mini = i;
        for(int j = i+1;j<n;j++){
            if(arr[mini]>arr[j])
            mini = j;
        }
        // if(mini!=i)
        swap(arr[i],arr[mini]);
    }
}
```
> # Bubble sort
at one iteration we put the largest element at the last
```cpp

void bubbleSort(int arr[],int n){

     for (int i = n - 1; i > 0; i--)
            for (int j = i - 1; j >= 0; j--)
                if (arr[i] < arr[j])
                    swap(arr[i], arr[j]);
}
```
> # Insertion Sort
take one by one element and put it at the right position

```cpp
void ins_sort(int arr[],int n){

    for (int i = 0; i < n; i++) {
            int j = i;
            while (j > 0 && arr[j - 1] > arr[j]) {
                swap(arr[j - 1], arr[j]);
                j--;
            }
        }
}
```
> # quick Sort
in this sort each time we select a pivot element ans , based upon pivod the divide whole arr in two part
at one iteration we get the actual position of pivot element

```cpp
//second function
 int position(vector<int>& nums, int l, int h) {
        int i = l, j = h;
        int pivet = nums[l];
        while (i < j) {
            while (nums[i] <= pivet && i <h ) {
                i++;
            }

            while (nums[j] > pivet && j >l ) {
                j--;
            }

            if (i < j)
                swap(nums[i], nums[j]);
        }
        swap(nums[j], nums[l]);
        return j;
    }
    // fist 
    void quickSort(vector<int>& nums, int low, int high) {
        if (low < high) {
            int j = position(nums, low, high);
            quickSort(nums, low, j - 1);
            quickSort(nums, j + 1, high);
        }
    }
    // main function
  void sortArray(vector<int>& nums) {
        // quick sort
        quickSort(nums, 0, nums.size() - 1);
       
    }
```

> # Merge sort 
work on divide and concur mathod

```cpp
// merge function
 void merge(int arr[], int l, int m, int r)
{
    int left = l, right = m + 1;
    vector<int> temp;
    while (left <= m && right <= r)
    {
        if (arr[left] < arr[right])
        {
            temp.push_back(arr[left]);
            left++;
        }
        else
        {
            temp.push_back(arr[right]);
            right++;
        }
    }
    while (left <= m)
    {
        temp.push_back(arr[left]);
        left++;
    }
    while (right <= r)
    {
        temp.push_back(arr[right]);
        right++;
    }
// copy temp to arr 
    for (int i = l; i <= r; i++)
    {
        arr[i] = temp[i - l];
    }
}
// main function

void mergeSort(int arr[], int l, int r)
{
    if (l >= r)
        return;
    int m = (l + r) / 2;
    mergeSort(arr, l, m);
    mergeSort(arr, m + 1, r);
    merge(arr, l, m, r);
}
```

> Counting Sort
![](./counting%20sort.png)
```cpp
 string countSort(string arr){
        
      vector<int>cnt(26,0);
        for(auto x:arr)
            cnt[x-'a']++;
       
       string ans ="";
       for(int i=0;i<26;i++){
            char ch = 'a'+i;
           while(cnt[i]--){
               ans+=ch;
           }
       }
        return ans;
    }
    
```

# heap Sort 
using max heap
```cpp
void heapSort(int arr, int n){
  priority_queue<int> q(arr,arr+n);
        int i = n-1;
        while(!q.empty()){
            arr[i--] = q.top();
            q.pop();
        }
}
```
using min heap 

```cpp

void HeapSort(int arr[],int n){
      priority_queue<int,vector<int>,greater<int>> q(arr,arr+n);
        int i = 0;
        while(!q.empty()){
            arr[i++] = q.top();
            q.pop();
            
        }
}
```

# Redix Sort 
in this sorting algorithm 
1. first we find the max element in the arr
2. find the no of digit in max element using log10
3. call the redix function of each digit 1 , 2 ,3, 4,...up to no of digit
3. in redix function first we make temp list of size 10 
4.  int temp list at x index all value will store which has k digit is equal to x
5. each list element one by one add in ans vector 
6. make a copy in arr of ans

```cpp
// function for sorting base upon k digit
void redix(int arr[], int n, int k) {
    // Create a list of vectors for sorting based on the k-th digit
    vector<int> temp[10];
    
    // Calculate the divisor for extracting the k-th digit
    int div = pow(10, k - 1);
    
    for (int i = 0; i < n; i++) {
        int num = arr[i];
        num /= div;
        temp[num % 10].push_back(arr[i]);
    }
    
    // Reconstruct the sorted array
    vector<int> ans;
    for (auto x : temp) {
        for (auto y : x) {
            ans.push_back(y);
        }
    }
    
    // Update the original array
    for (int i = 0; i < n; i++) {
        arr[i] = ans[i];
    }
}

// main function 
void radixSort(int arr[], int n) {
    // Find the maximum value in the array
    int maxi = INT_MIN;
    for (int i = 0; i < n; i++) {
        maxi = max(maxi, arr[i]);
    }
    
    // Calculate the number of digits in maxi
    int digit = log10(maxi) + 1;
    
    // Call the redix function for each digit position
    for (int i = 1; i <= digit; i++) {
        redix(arr, n, i);
    }
}
```

# Bucket Sort 


> # Time complexity 
![](./time%20complexity.jpg)