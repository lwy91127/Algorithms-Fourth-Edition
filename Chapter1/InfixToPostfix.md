#表达式中序转后序

<pre><code>
public class InfixToPostfix {
	 private static HashMap< Character,Integer> priority=new HashMap< Character,Integer>(){  
       {  
            put('+', 1);  
            put('-', 1);  
            put('/', 2);  
            put('*', 2);  
            put('(', 0);  
        }  
    };
	public static void main(String[] args) {
		Stack< Character> stack = new Stack< Character>();
		while(!StdIn.isEmpty())
		{
			char c = StdIn.readChar();
			switch(c)
			{
				case '(':
					stack.push(c);
					break;
				case '+':
					while(!stack.isEmpty() && priority.get(stack.peek()) >= priority.get(c))
					{
						StdOut.print(stack.pop());
					}
					stack.push(c);
					break;
				case '-':
					while(!stack.isEmpty() && priority.get(stack.peek()) >= priority.get(c))
					{
						StdOut.print(stack.pop());
					}
					stack.push(c);
					break;
				case '*':
					while(!stack.isEmpty() && priority.get(stack.peek()) >= priority.get(c))
					{
						StdOut.print(stack.pop());
					}
					stack.push(c);
					break;
				case '/':
					while(!stack.isEmpty() && (priority.get(stack.peek()) >= priority.get(c)))
					{
						StdOut.print(stack.pop());
					}
					stack.push(c);
					break;
				case ')':
					while(!stack.isEmpty() && stack.peek() != '(')
					{
						StdOut.print(stack.pop());
					}
					stack.pop();	
					break;
				default:
					StdOut.print(c);
					break;
			}
		}
		if(!stack.isEmpty())
		{
			for(char a : stack)	
				StdOut.print(a);
		}
		StdOut.println();
	}
}
</pre></code>