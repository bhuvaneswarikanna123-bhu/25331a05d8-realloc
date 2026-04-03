# 25331a05d8-realloc
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *arr;
    int n, new_size, i;
    printf("Enter initial number of elements: ");
    scanf("%d", &n);
   arr = (int *)malloc(n * sizeof(int));
    if (arr == NULL) {
    printf("Memory allocation failed!\n");
        return 1;
    }
    printf("Enter %d elements:\n", n);
    for(i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
     printf("\nOriginal array:\n");
    for(i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n\nEnter new size of array: ");
    scanf("%d", &new_size);
     arr = (int *)realloc(arr, new_size * sizeof(int));

    if (arr == NULL) {
        printf("Reallocation failed!\n");
        return 1;
    }

    if (new_size > n) {
        printf("Enter %d more elements:\n", new_size - n);
        for(i = n; i < new_size; i++) {
            scanf("%d", &arr[i]);
        }
    }

    printf("\nUpdated array:\n");
    for(i = 0; i < new_size; i++) {
        printf("%d ", arr[i]);
    }


    free(arr);

    return 0;
}
