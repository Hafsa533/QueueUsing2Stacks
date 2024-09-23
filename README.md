# QueueUsing2Stacks
Simple Program 

class Stack {
    private int[] arr;
    private int top;
    public int capacity = 100;

    public Stack() {
        arr = new int[capacity];
        top = -1;
    }

    public boolean isEmpty() {
        return top == -1;
    }

    public boolean isFull() {
        return top == capacity - 1; // fix here
    }

    public void push(int data) {
        if (isFull()) {
            System.out.println("Stack overflow");
        } else {
            arr[++top] = data;
        }
    }

    public int pop() {
        if (isEmpty()) {
            System.out.println("Stack underflow");
            return -1; // indicate an error when underflow occurs
        } else {
            return arr[top--]; // return the element before decrementing top
        }
    }

    public int peek() { // changing top() to peek() to return the top element
        if (isEmpty()) {
            System.out.println("Stack is Empty");
            return -1; // return -1 to indicate error
        } else {
            return arr[top];
        }
    }

    public void printData() {
        for (int i = 0; i <= top; i++) {
            System.out.print(arr[i] + " , ");
        }
    }
}



class MyQueue {

        Stack stack1;
        Stack stack2;


        public MyQueue() {
            stack1 = new Stack();
            stack2 = new Stack();
        }

        public void push(int x) {
            stack1.push(x);
        }

        public int pop() {
            if (stack2.isEmpty()) {
                while (!stack1.isEmpty()) {
                    stack2.push(stack1.pop());
                }
            }
           return stack2.pop();
        }

        public int peek() {
            if (stack2.isEmpty()) {
                while (!stack1.isEmpty()) {
                    stack2.push(stack1.pop());
                }
            }

            return stack2.peek();

        }

        public boolean empty() {

            return stack1.isEmpty() && stack2.isEmpty();

        }
    }


