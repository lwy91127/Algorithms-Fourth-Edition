#表达式中序转前序

<pre><code>public class InfixToPre {
	private static HashMap<Character,Integer> priority=new HashMap<Character,Integer>()
	{  
		{  
	        put('+', 1);  
	        put('-', 1);  
	        put('/', 2);  
	        put('*', 2);  
	        put('(', 0);
	        put(')', 0);  
    	}  
	};
	public static void main(String[] args) {
		Stack<Character> stack = new Stack<Character>();
		Stack<Character> result = new Stack<Character>();
		while(!StdIn.isEmpty())
		{
			String s = StdIn.readString();
			char[] reverseStr = reverseStr(s);
			for(char c : reverseStr)
			{
				switch(c)
				{
					case ')':
						stack.push(c);
						break;
					case '+':
					case '-':
					case '*':
					case '/':
						while(!stack.isEmpty() && priority.get(c) < priority.get(stack.peek()))
						{
							result.push(stack.pop());
							//StdOut.print(stack.pop());
						}
						stack.push(c);
						break;
					case '(':
						while(!stack.isEmpty() && stack.peek()!=')')
						{
							result.push(stack.pop());
							//StdOut.print(stack.pop());
						}
						stack.pop();
						break;
					default:
						result.push(c);
						break;
				}
			}
			if(!stack.isEmpty())
			{
				for(char a:stack)
					result.push(a);
			}
			for(char c:result)
				StdOut.print(c);
		}
	}
	private static char[] reverseStr(String s) {
		char[] cs = s.toCharArray();
		int i = 0;
		int j = s.length() -1;
		while(i < j)
		{
			char temp = cs[i];
			cs[i] = cs[j];
			cs[j] = temp;
			i++;
			j--;
		}
		return cs;
	}
}</code></pre>