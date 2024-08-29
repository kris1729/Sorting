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