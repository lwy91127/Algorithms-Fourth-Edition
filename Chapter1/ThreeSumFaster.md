#ThreeSumFaster

```java
public class ThreeSumFaster {
	public static void main(String[] args) {
		int[] a = In.readInts("f:/1Kints.txt");
		Arrays.sort(a);
		int sum = 0;
		for(int i = 0;i< a.length;i++)
		{
			sum += count(i,a);
		}
		System.out.println(sum/3);
	}
	private static int count(int i,int[] a) {
		int l = 0;
		int r = a.length-1;
		int cnt = 0;
		while(l< r)
		{
			if(a[l] + a[r] > -a[i])
				r--;
			else if(a[l] + a[r] < -a[i])
				l++;
			else
			{
				cnt++;
				r--;
				l++;
			}
		}
		return cnt;	
	}
}
```