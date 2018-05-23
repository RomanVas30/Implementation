## С++:

[Моя реализация](https://github.com/RomanVas30/List)

## Java:

class ListElement {
    ListElement next;    
    int data;            
}

class List {
    private ListElement head;       
    private ListElement tail;      
 
> Добавить спереди
    void addFront(int data)           
    {
        ListElement a = new ListElement();  
        a.data = data;              
                                    
        if(head == null)           
        {                          
            head = a;              
            tail = a;
        }
        else {
            a.next = head;          
            head = a;              
        }
    }
 
> Добавление в конец списка
    void addBack(int data) {          
        ListElement a = new ListElement();  
        a.data = data;
        if (tail == null)           
        {                           
            head = a;               
            tail = a;
        } else {
            tail.next = a;          
            tail = a;               
        }
    }
 
 > Печать списка
    void printList()                
    {
        ListElement t = head;         
        while (t != null)           
        {
            System.out.print(t.data + " "); 
            t = t.next;                    
        }
    }
 
 
> Удаление элемента
    void delEl(int data)          
    {
        if(head == null)       
            return;            
 
        if (head == tail) {     
            head = null;        
            tail = null;
            return;          
        }
 
        if (head.data == data) {  
            head = head.next;      
            return;                
        }
 
        ListElement t = head;       
        while (t.next != null) {  
            if (t.next.data == data) {
                if(tail == t.next)     
                {
                    tail = t;           
                }
                t.next = t.next.next;   
                return;                 
            }
            t = t.next;                
        }
    }
}

## Python:

class Node:
    def __init__(self, value = None, next = None):
        self.value = value
        self.next = next


import copy
import random 
 
class LinkedList:
    def __init__(self):
        self.first = None
        self.last = None
        self.length = 0
 
    def __str__(self):
        if self.first != None:
            current = self.first
            out = 'LinkedList [\n' +str(current.value) +'\n'
            while current.next != None:
                current = current.next
                out += str(current.value) + '\n'
            return out + ']'
        return 'LinkedList []'
 
    def clear(self):
        self.__init__()

> Функция для определения длины списка:
def Len(self):
    self.length =0
    if self.first != None:
        self.length +=1
        current = self.first
        while current.next != None:
            current = current.next
            self.length +=1
    return self.length

> Добавление элементов в начало списка:
def Push(self, x):
    if self.first == None:
        self.first = Node(x,None)
        self.last = self.first
    else:
        self.first = Node(x,self.first)

> Добавление элементов в конец списка:
def add(self, x):
    if self.first == None:
        self.first = Node(x, None)
        self.last = self.first
    elif self.last == self.first:
        self.last = Node(x, None)
        self.first.next = self.last
    else:
        current = Node(x, None)
        self.last.next = current
        self.last = current

> Вставка элемента в список:
def InsertNth(self,i,x):
    if (self.first == None):
        self.first = Node(x,self.first)
        self.last = self.first.next
        return
    if i == 0:
      self.first = Node(x,self.first)
      return
    curr=self.first
    count = 0
    while curr != None:
        if count == i-1:
          curr.next = Node(x,curr.next)
          if curr.next.next == None:
            self.last = curr.next
          break
        curr = curr.next

> Удаление головы:
def Pop(self):
    oldhead=self.first
    if oldhead==None:
        return None
    self.first=oldhead.next
    if self.first==None:
        self.last=None
    return oldhead.value

> Удаление элемента из списка:
def Del(self,i):
    if (self.first == None):
      return
    old = curr = self.first
    count = 0
    if i == 0:
      self.first = self.first.next
      return
    while curr != None:
        if count == i:
          if curr.next == self.last:
            self.last = curr
            break
          else:
            old.next = curr.next 
          break
        old = curr  
        curr = curr.next
        count += 1

> Вставка элемента в отсортированный список:
def SortedInsert(self,x):
    if (self.first == None):
      self.first = Node(x,self.last)
      return
    if self.first.value > x:
      self.first = Node(x,self.first)
      return
    old = curr = self.first
    while curr != None:
        if curr.value > x:
          curr = Node(x,curr)
          old.next = curr
          return
        old = curr
        curr = curr.next
    curr = Node(x,None)        
    old.next = curr

> Удаление повторяющихся значений:
def RemoveDuplicates(self):
    if (self.first == None):
        return
    old = curr = self.first
    while curr != None:
        _del = 0 
        if curr.next != None:
            if curr.value == curr.next.value:
              curr.next = curr.next.next
              _del = 1
        if _del == 0:
          curr = curr.next
