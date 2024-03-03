# Lab 1


```csharp
using System;
using System.Collections.Generic;

namespace replit{
  class Program {
  public static void Main (string[] args) {
    
    int[] arr = { 0, 1, 2, 3, 2, 6, 1, 6, 3, 2 };
    int[] arrOdd = { 1, 3, 5, 7, 9 };
    int[] arrEven = { 0, 2, 4, 6, 8 };
    int[,] arr1 = new int[3, 3] {
      { 1, 2, 3 },
      { 4, 5, 6 },
      { 7, 8, 9 }
    };
    int[,] arr2 = new int[3, 3] {
      { 10, 11, 12 },
      { 13, 14, 15 },
      { 16, 17, 18 }
    };

    Console.WriteLine("Question#1");
    CountDuplicate(arr);
    Console.WriteLine("\nQuestion#2");
    MergeAndSort(arrOdd, arrEven);
    Console.WriteLine("\nQuestion#3");
    SumOf3By3(arr1, arr2);
    Console.WriteLine();
  }

  public static void CountDuplicate(int[] arr)
  {
    Dictionary<int, int> countMap = new Dictionary<int, int>();
    foreach (int num in arr)
    {
      if (countMap.ContainsKey(num))
      {
        countMap[num] += 1;
      }
      else
      {
        countMap[num] = 1;
      }
    }

    foreach (var cn in countMap)
    {
      Console.WriteLine($"{cn.Key}: {cn.Value}");
    }

  }

  public static void MergeAndSort(int[] arr1, int[] arr2)
  {
    // int[] mergedArr = arr1.Concat(arr2).ToArray();
    int[] mergedArr = new int[arr1.Length + arr2.Length];

    for (int i = 0; i < arr1.Length; i++)
    {
      mergedArr[i] = arr1[i];
    }
    for (int i = 0; i < arr2.Length; i++)
    {
      mergedArr[arr1.Length + i] = arr2[i];
    }
    //Array.Sort(mergedArr);

    int[] sortedArr = BubbleSort(mergedArr);

    foreach (int num in sortedArr)
    {
      Console.Write($"{num}, ");
    }

    Console.WriteLine();
  }

  public static int[] BubbleSort(int[] arr)
  {
    for (int i = 0; i < arr.Length; i++)
    {
      for (int j = 0; j < i; j++)
      {
        if (arr[j] > arr[i])
        {
          (arr[i], arr[j]) = (arr[j], arr[i]);
        }
      }
    }
    return arr;
  }

  public static void SumOf3By3(int[,] arr1, int[,] arr2)
  {
    int[,] result = new int[3, 3];

    for (int i = 0; i < 3; i++) {
      for (int j = 0; j < 3; j++) {
        result[i, j] = arr1[i, j] + arr2[i, j];
      }
    }

    Console.WriteLine("The sum of the two 3x3 arrays is:");
    for (int i = 0; i < 3; i++) {
      for (int j = 0; j < 3; j++) {
        Console.Write(result[i, j] + " ");
        }
      Console.WriteLine();
      }
    }
  }
}
```