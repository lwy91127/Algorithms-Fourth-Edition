#Insertion Sort

```java
public static void sort(Comparable[] a) {
		int j;
		for(int i = 1; i < a.length; i++)
		{	
			Comparable tmp = a[i];
			for( j = i;j > 0 && less(tmp,a[j-1]);j--)
				a[j] = a[j-1];
			a[j] = tmp;
		}
}
```