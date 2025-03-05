#include <stdio.h>
int row,col,pos;

void findSecondSmallest(int arr[], int n) {
    if (n < 2) {
        printf("Array must have at least two elements.\n");
        return;
    }

    int smallest, second_smallest;

    // Initialize smallest and second_smallest with the first two elements properly
    if (arr[0] < arr[1]) {
        smallest = arr[0];
        second_smallest = arr[1];
    } else {
        smallest = arr[1];
        second_smallest = arr[0];
    }

    for (int i = 2; i < n; i++) {
        if (arr[i] < smallest) {
            second_smallest = smallest;
            smallest = arr[i];
        } else if (arr[i] < second_smallest && arr[i] != smallest) {
            second_smallest = arr[i];
        }
    }

    if (smallest == second_smallest) {
        printf("No second smallest element (all elements are equal).\n");
    } else {
        printf("The second smallest element is: %d\n", second_smallest);
    }
}
void leftdiagonal(int m[row][col],int row,int col){
    int sum=0;
    for (int i=0;i<row;i++){
        sum+=m[i][i];
    }
    printf("sum is %d",sum);


}
void sumrc(int m[row][col],int row,int col){
    int rs=0,cs=0;
    for (int i=0;i<row;i++){
            for (int j=0;j<col;j++){
                    rs+=m[i][j];


      }
     printf("\nsum of %d th row is %d",i,rs);
    }
  for (int i=0;i<col;i++){
            for (int j=0;j<row;j++){
                    cs+=m[i][j];


    }
    printf("\nsum of %d th col is %d",i,cs);
  }
}


void countDuplicates(int arr[], int n) {
    int count = 0;
    int visited[n];


    for (int i = 0; i < n; i++) {
        visited[i] = 0;
    }

    for (int i = 0; i < n; i++) {
        if (visited[i] == 1)
            continue;

        int duplicateFound = 0;

        for (int j = i + 1; j < n; j++) {
            if (arr[i] == arr[j]) {
                visited[j] = 1;
                duplicateFound = 1;
            }
        }

        if (duplicateFound) {
            count++;
        }
    }

    printf("\nTotal number of duplicate elements: %d\n", count);
}
void findSecondLargest(int arr[], int n) {
    if (n < 2) {
        printf("Array must have at least two elements.\n");
        return;
    }

    int largest, second_largest;

    if (arr[0] > arr[1]) {
        largest = arr[0];
        second_largest = arr[1];
    } else {
        largest = arr[1];
        second_largest = arr[0];
    }

    for (int i = 2; i < n; i++) {
        if (arr[i] > largest) {
            second_largest = largest;
            largest= arr[i];
        } else if (arr[i] > second_largest && arr[i] != largest) {
            second_largest = arr[i];
        }
    }

    if (largest == second_largest) {
        printf("No second largest element (all elements are equal).\n");
    } else {
        printf("The second largest element is: %d\n", second_largest);
    }
}

void deleteElement(int arr[], int *n, int pos) {
    if (pos < 1 || pos > *n) {
        printf("Invalid position! Please enter a position between 1 and %d.\n", *n);
        return;
    }

    for (int i = pos - 1; i < *n - 1; i++) {
        arr[i] = arr[i + 1];
    }

    (*n)--;


    printf("Array after deletion:\n");
    for (int i = 0; i < *n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}




int main() {
    int arr[] = {5, 2, 8, 1, 3, 1,8,2,0};
    int n = sizeof(arr) / sizeof(arr[0]);
    int row=col=3,pos=3;

    findSecondSmallest(arr, n);
    int m[3][3]={1,2,3,
               4,5,6,
               5,5,7};
    leftdiagonal(m,row,col);
    sumrc(m,row,col);
    countDuplicates(arr,n);
    findSecondLargest(arr, n);
    deleteElement(arr,&n,pos);

    return 0;

}


