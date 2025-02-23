Deque can be used to implement a stack and queue. One simply needs to understand how deque can made to work as a stack or a queue.
![image](https://github.com/user-attachments/assets/76ba2546-79aa-4a99-88f7-8dbed3643b07)
**Solution**
```
class node:
    def __init__(self,val):
        self.val = val
        self.prev = None
        self.next = None
    
class Deque:
    def __init__(self):
        self.head = self.tail = None
    
    def isEmpty(self):
        if (self.head == None): return True
        return False
    
    def insert_first(self,element):
        newP = node(element)
        if self.head == None: 
            self.head = self.tail = newP
            return
        newP.next = self.head
        self.head.prev = newP
        self.head = newP
    
    def insert_last(self,element):
        newP = node(element)
        if self.head == None: 
            self.head = self.tail = newP
            return
        newP.prev = self.tail
        self.tail.next = newP
        self.tail = newP
        
    def size(self):
        curr = self.head
        len = 0
        while curr != None:
            len += 1
            curr = curr.next
        return len
        
    def remove_first(self):
        if self.isEmpty(): 
            print('List is Empty')
            return
        self.head = self.head.next
        if self.head != None: self.head.prev = None
        
    def remove_last(self):
        if self.isEmpty():
            print('List is Empty')
            return
        self.tail =  self.tail.prev
        if self.tail != None: self.tail.next = None
        
    def display(self):
        if self.isEmpty():
            print('List is Empty')
            return
        curr = self.head
        while curr != None:
            print(curr.val,end = ' ')
            curr = curr.next
        print()
            
class Stack:
    def __init__(self):
        self.stack = Deque()
    
    def push(self,element):
        self.stack.insert_last(element)
    
    def pop(self):
        self.stack.remove_last()
        
    def size(self):
        return self.stack.size()
    
    def display(self):
        self.stack.display()
        
class Queue:
    def __init__(self):
        self.que = Deque()
    
    def enqueue(self,element):
        self.que.insert_last(element)
    
    def dequeue(self):
        self.que.remove_first()
        
    def size(self):
        return self.que.size()
        
    def display(self):
        self.que.display()
            
            
stk = Stack() 

 # push 7 and 8 at top of stack
stk.push(7) 
stk.push(8) 
print("Stack: ") 
stk.display() 

 # pop an element
stk.pop() 
print("Stack: ") 
stk.display() 

 # Object of Queue
que = Queue() 

 # Insert 12 and 13 in queue
que.enqueue(12) 
que.enqueue(13) 
print("Queue: ") 
que.display() 

 # Delete an element from queue
que.dequeue() 
print("Queue: ") 
que.display() 

print("Size of stack is ",stk.size()) 
print("Size of queue is ", que.size()) 

```
