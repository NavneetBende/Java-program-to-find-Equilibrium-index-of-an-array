Equilibrium index of an array in Java
Here we will learn about Java program to find Equilibrium index of an array in java , it is an index such that the sum of elements at lower indexes is equal to the sum of elements at higher indexes.

Sum of elements at lower indexes = Sum of elements at higher indexes.

Equilibrium index of an array in Java
In this section we will learn about basic knowledge which we need to know before coding the above Program. So we must have knowledge of what is an array? 

What is an array?
An array is a data structure, it is collection of similar data elements which is stored at contiguous memory locations in which each data element can be accessed directly by only using its index number.
 
How to declare an array?
To declare an array in C,a programmer specifies the type of the elements and the number of elements required by an array as follows − This is called a single-dimensional array. The array Size must be an integer constant greater than zero and type can be any valid C data type. For example, to declare a 10-element array called balanceof type double, use this statement − Here balanceis a variable array which is sufficient to hold up to 10 double numbers.
 
About Java language:-
Java is class-based, object-oriented programming language and used for Internet-based applications. Java is a high-level
language.
Method Discussed :
Method 1 : Using Nested loops.
Method 2 : Using single for loop
Method 3 : Using Binary search concept.
Method 1 :
Run a loop from index 0 to n.
Create a variable say left_sum =0, to find the left indexed value sum.
Run a loop from index 0 to i to find left_sum.
Similarly, declare right_sum = 0,
Run a loop from index i to n, and find right_sum.
If left_sum == right_sum, return i.
Method 1 : Code in Java
import java.util.*;

public class PrepInsta
{
    static int equilibrium_index(int arr[], int n)
    {
        int sum = 0;
        int leftsum = 0;

        for (int i = 0; i < n; ++i)
            sum += array[i];

        for (int i = 0; i < n; ++i) {
            sum -= array[i];

            if (leftsum == sum)
                return i;

            leftsum += array[i];
        }

        return -1;
    }

    public static void main(String[] args)
    {
        int arr[] = { 1,2,3,4,5,1,3,2,4 };
        int arr_size = arr.length;
        System.out.print("Equilibrium Index : ");
        System.out.println(equilibrium_index(arr, arr_size));
    }
}
Output-
Equilibrium index : 4
Method 2 :
In this method we will use single loop to find the equilibrium point in the array.

Time-Complexity : O(n)
Space-Complexity : O(1)
Method 2 : Code in Java
import java.util.*;

public class Main
{
    static int equilibrium_index(int arr[], int n)
    {
        int result = -1;
  
        for(int i=0; i<n; i++){
    
        int left_sum =0;
        for(int j=0; j<i; j++)
            left_sum += arr[i];
    
        int right_sum =0;
        for(int j=i+1; j<n; j++)
            right_sum += arr[i];
    
        if(right_sum == left_sum)
            return i;
          
        }
        
        return -1;
    }

    public static void main(String[] args)
    {
        int arr[] = { 1,2,3,4,5,1,3,2,4 };
        int arr_size = arr.length;
        System.out.print("Equilibrium Index : ");
        System.out.println(equilibrium_index(arr, arr_size));
    }
}
Output-
Equilibrium index : 4
Method 3 :
In this method we will discuss the binary search concept to find the equilibrium index.

Method 3: Code in Java
import java.util.*;

public class Main
{
    static void find(int arr[],  int n)
    {
        int mid = n / 2;
        int leftSum = 0, rightSum = 0;
 
        //calculation sum to left of mid
        for (int i = 0; i < mid; i++){
            leftSum += arr[i];
        }
        //calculating sum to right of mid
        for (int i = n - 1; i > mid; i--)
        {
            rightSum += arr[i];
        }
 
        if (rightSum > leftSum)
        {
            while (rightSum > leftSum && mid < n - 1)
            {
                rightSum -= arr[mid + 1];
                leftSum += arr[mid];
                mid++;
            }
        }
        else
        {
            while (leftSum > rightSum && mid > 0)
            {
                rightSum += arr[mid];
                leftSum -= arr[mid - 1];
                mid--;
            }
        }
 
        if (rightSum == leftSum)
        {
            System.out.print("Equilibrium index : "+ mid);
            return;
        }
 
        System.out.print("Equilibrium index : " + -1);
    }

    public static void main(String[] args)
    {
        int arr[] = { 1,2,3,4,5,1,3,2,4 };
        int arr_size = arr.length;
        
        find(arr, arr_size);
    }
}
Output-
Equilibrium index : 4
