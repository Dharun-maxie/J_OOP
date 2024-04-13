### Quick Sort

*One of the Most used Sorting `Algorithm`. Which is also used as an inbuild sorting `Algorithm` in `Intellij`.*

![[Qsort.jpg]]
![[Qsort1.jpg]]


*Let's Implement this into Code.*

```java
public class Main
{
	public static void main(String[] args)
	{
		int[] arr={6,2,3,5,9,8,7,1};
		
		Qsort(arr,0,arr.length-1);
		
		System.out.println(Arrays.toString(arr));
	}
	public static void Qsort(int[] arr,int l,int h)
	{
		if(l>h)
		{
			return;
		}
		int partion=Partion(arr,l,h);
		
		Qsort(arr,l,partion-1);
		Qsort(arr,partion+1,h);
	}
	private static int Partion(int[] arr,int l,int h)
	{
		int low=l-1;  
		for(int i=l;i<h;i++)  
		{  
		    if(arr[h] > arr[i]) {  
		        low++;  
		        int temp = arr[i];  
		        arr[i] = arr[low];  
		        arr[low] = temp;  
		    }  
		}  
		int temp=arr[low+1];  
		arr[low+1]=arr[h];  
		arr[h]=temp;  
		
		return low+1;
	}
}
```

### Merge Sort

*`Merge Sort` is known for it `complexity`. but in my point of view it is easy. It take `worst Time complexity` of `0(log N).`*

```java 
public int[] Msort(int[] arr)  
{  
    if(arr.length == 1 || arr.length == 0)  
        return arr;  
  
    int m= arr.length/2;  
  
    int[] F = Msort(Arrays.copyOfRange(arr,0,m));  
    int[] S = Msort(Arrays.copyOfRange(arr,m,arr.length));  
  
    return MergeArray(F,S);  
}  
  
private int[] MergeArray(int[] f, int[] s) {  
    int[] Ans=new int[f.length+s.length];  
  
    int FIndex=0,SIndex=0,AIndex = 0;  
  
    while(FIndex < f.length && SIndex < s.length)  
    {  
        if(f[FIndex] < s[SIndex])  
        {  
            Ans[AIndex] = f[FIndex];  
            FIndex++;  
        }  
        else  
        {  
            Ans[AIndex] = s[SIndex];  
            SIndex++;  
        }  
        AIndex++;  
    }  
    while(FIndex < f.length)  
        Ans[AIndex++] = f[FIndex++];  
    while(SIndex < s.length)  
        Ans[AIndex++] = s[SIndex++];  
  
    return Ans;  
}
```
