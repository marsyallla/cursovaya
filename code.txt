#include <stdio.h>
#include <stdlib.h>
void addElement(int **array, int *size,int *capacity,int value)
{
    if (*size >= *capacity)
    {
        *capacity = (*capacity == 0) ? 1 : (*capacity * 2);
        *array = realloc(*array, (*capacity) * sizeof(int));}
        if (*array == NULL)
        {
            printf("Array over\n");
            exit(1);
        }

        (*array)[*size] = value;
        (*size)++;
    }
    int compare(const void *a, const void *b)
    {
        return (*(int*)a - *(int*)b);
    }
    int search (int left, int right, int key, int array[] )
    {
        if (left>right)
            return -1;

        int middle=(left+right)/2;

        if (key==array[middle])
            return middle;
        if (key>array[middle])
            return  search(middle+1,right, key,array);
        else return search(left,middle-1, key, array );
    }


    int main()
    {
        int aim,N, value;
        int *array=NULL;
        int size=0;
        int capacity=0;
        if (scanf("%d", &N) != 1 || N <= 0 )
        {
            printf("No");
            return 1;
        }

        for(int i=0; i<N; i++)
        {
            if (scanf("%d", &value) != 1)
            {
                printf("No");
                 free(array);
        return 1;
            }


            addElement(&array, &size,&capacity, value);
        }
if (size>0){
        qsort(array,size, sizeof(int), compare);
        //отсортированный массив
        for (int i = 0; i < size; i++)
        {
            printf("%d ", array[i]);
        }
        printf("\n");

        if (scanf("%d", &aim)==1)
        {

        int result=search(0, size-1, aim, array);
        if (result == -1)
        {
            printf("Nothing");
        }
        else
        {
            printf("%d: found", result);
        }}}
        free(array);
        return 0;
    }
