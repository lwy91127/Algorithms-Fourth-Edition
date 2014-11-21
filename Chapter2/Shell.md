#Shell Sort

```java
public static void sort(Comparable[] a) {
		int j;
		int N = a.length;
		int step = N/2;
		while(step >= 1)
		{
			for(int i = step; i < N; i++)
			{	
				Comparable tmp = a[i];
				for( j = i - step;j >= 0 && less(tmp,a[j]);j -=step)
					a[j + step] = a[j];
				a[j+step] = tmp;
			}
			step = step/2;
		}
}
```