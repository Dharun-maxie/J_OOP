
### Bubble Sort

`Bubble Sort` is one of the most Famous and Easy Sorting Algorithm. Which Take O(N) 2 `Time Complexity`. This is the Implementation of `Bubble Sort`

```java
public static void Bsort(int[] arr)
{
	for(int i=0;i< arr.length-1;i++)
	{
		int check=0;
		for(int j=1;j<arr.length-i;j++)
		{
			if (arr[j-1] > arr[j])
			{
				int temp=arr[j-1];
				arr[j-1]=arr[j];
				arr[j]=temp;
				check++;
			}
		}
		if(check == 0)
			break;
	}
}
```

### Selection Sort

`Selection Sort` Take an Biggest or Lowest Number and `Swap` it with it correct `index`.

```java
public static void Ssort(int[] arr)
{
	for(int i=0;i< arr.length-1;i++)
	{
		int smallVal=Integer.MAX_VALUE;
		for(int j=i;j< arr.length;j++)
		{
			if (smallVal > arr[j])
			{
				smallVal=j;
			}
		}
		int temp=arr[smallVal];
		arr[smallVal]=arr[i];
		arr[i]=arr[smallVal];
	}
}
```

### Insertion Sort

`Insertion Sort` is Somewhat Same as the Previous `Algorithm`.

##### `Methodology`

![[ISort.jpg]]

*The Element Assigning Part.*

![[ISort2.jpg]]

*Implementation of the code.*

```java
public int[] Isort(int[] arr)
{
	for(int i=1; i< arr.length; i++)
	{
		int elem=arr[i];
		int j=i-1;
		while(j>=0 && arr[j] > elem)
		{
			arr[j+1]=arr[j];
			j--;
		}
		arr[j+1] = elem;
	}
	return arr;
}
```

**That How Insertion Sort Work.** 