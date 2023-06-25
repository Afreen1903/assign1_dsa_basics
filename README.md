problem-1:
# Python3 implementation of simple method
# to find count of pairs with given sum.
 
# Returns number of pairs in arr[0..n-1]
# with sum equal to 'num'
 
 
def getPairsCount(arr, n, num):
 
    count = 0  # Initialize result
 
    # Consider all possible pairs
    # and check their sums
    for i in range(0, n):
        for j in range(i + 1, n):
            if arr[i] + arr[j] == num:
                count += 1
 
    return count
 
 
# Driver function
arr = [1, 5, 7, -1, 5]
n = len(arr)
num = 6
print("Count of pairs is",
      getPairsCount(arr, n, num))

problem-2:

# Iterative python program to reverse an array
  
# Function to reverse A[] from start to end
def reverseList(A, start, end):
    while start < end:
        A[start], A[end] = A[end], A[start]
        start += 1
        end -= 1
  
# Driver function to test above function
A = [1, 2, 3, 4, 5, 6]
print(A)
reverseList(A, 0, 5)
print("Reversed list is")
print(A)

problem-3:

# Python program to check if strings are rotations of
# each other or not

# Function checks if passed strings (str1 and str2)
# are rotations of each other
def areRotations(string1, string2):
	size1 = len(string1)
	size2 = len(string2)
	temp = ''

	# Check if sizes of two strings are same
	if size1 != size2:
		return 0

	# Create a temp string with value str1.str1
	temp = string1 + string1

	# Now check if str2 is a substring of temp
	# string.count returns the number of occurrences of
	# the second string in temp
	if (temp.count(string2)> 0):
		return 1
	else:
		return 0

# Driver program to test the above function
string1 = "AACD"
string2 = "ACDA"

if areRotations(string1, string2):
	print "Strings are rotations of each other"
else:
	print "Strings are not rotations of each other"

problem-4:

# String
myStr =input("enter a string")

# Looping
while myStr != "":
	slen0 = len(myStr)
	ch = myStr[0]
	myStr = myStr.replace(ch, "")
	slen1 = len(myStr)
	if slen1 == slen0-1:
		print ("First non-repeating character = ",ch)
		break;
	else:
		print ("No Unique Character Found!")

problem-5

# Recursive Python function to solve tower of hanoi


def TowerOfHanoi(n, from_rod, to_rod, aux_rod):
	if n == 0:
		return
	TowerOfHanoi(n-1, from_rod, aux_rod, to_rod)
	print("Move disk", n, "from rod", from_rod, "to rod", to_rod)
	TowerOfHanoi(n-1, aux_rod, to_rod, from_rod)


# Driver code
N = 3

# A, C, B are the name of rods
TowerOfHanoi(N, 'A', 'C', 'B')

problem-6:


# Python3 Program to convert postfix to prefix
 
# function to check if
# character is operator or not
 
 
def isOperator(x):
 
    if x == "+":
        return True
 
    if x == "-":
        return True
 
    if x == "/":
        return True
 
    if x == "*":
        return True
 
    return False
 
# Convert postfix to Prefix expression
 
 
def postToPre(post_exp):
 
    s = []
 
    # length of expression
    length = len(post_exp)
 
    # reading from right to left
    for i in range(length):
 
        # check if symbol is operator
        if (isOperator(post_exp[i])):
 
            # pop two operands from stack
            op1 = s[-1]
            s.pop()
            op2 = s[-1]
            s.pop()
 
            # concat the operands and operator
            temp = post_exp[i] + op2 + op1
 
            # Push string temp back to stack
            s.append(temp)
 
        # if symbol is an operand
        else:
 
            # push the operand to the stack
            s.append(post_exp[i])
 
    
    ans = ""
    for i in s:
        ans += i
    return ans
 
 
# Driver Code
if __name__ == "__main__":
 
    post_exp = "AB+CD-"
     
    # Function call
    print("Prefix : ", postToPre(post_exp))

problem-7:

# Python Program to convert prefix to Infix
def prefixToInfix(prefix):
	stack = []
	
	# read prefix in reverse order
	i = len(prefix) - 1
	while i >= 0:
		if not isOperator(prefix[i]):
			
			# symbol is operand
			stack.append(prefix[i])
			i -= 1
		else:
		
			# symbol is operator
			str = "(" + stack.pop() + prefix[i] + stack.pop() + ")"
			stack.append(str)
			i -= 1
	
	return stack.pop()

def isOperator(c):
	if c == "*" or c == "+" or c == "-" or c == "/" or c == "^" or c == "(" or c == ")":
		return True
	else:
		return False

# Driver code
if __name__=="__main__":
	str = "*-A/BC-/AKL"
	print(prefixToInfix(str))
	
problem-8:

# Python3 program to check for
# balanced brackets.

# function to check if
# brackets are balanced


def areBracketsBalanced(expr):
	stack = []

	# Traversing the Expression
	for char in expr:
		if char in ["(", "{", "["]:

			# Push the element in the stack
			stack.append(char)
		else:

			# IF current character is not opening
			# bracket, then it must be closing.
			# So stack cannot be empty at this point.
			if not stack:
				return False
			current_char = stack.pop()
			if current_char == '(':
				if char != ")":
					return False
			if current_char == '{':
				if char != "}":
					return False
			if current_char == '[':
				if char != "]":
					return False

	# Check Empty Stack
	if stack:
		return False
	return True


# Driver Code
if __name__ == "__main__":
	expr = "{()}[]"

	# Function call
	if areBracketsBalanced(expr):
		print("Balanced")
	else:
		print("Not Balanced")

problem-9:

class Stack:
    def __init__(self):
        self.items = []
 
    def is_empty(self):
        return self.items == []
 
    def push(self, data):
        self.items.append(data)
 
    def pop(self):
        return self.items.pop()
 
    def display(self):
        for data in reversed(self.items):
            print(data)
 
def insert_at_bottom(s, data):
    if s.is_empty():
        s.push(data)
    else:
        popped = s.pop()
        insert_at_bottom(s, data)
        s.push(popped)
 
 
def reverse_stack(s):
    if not s.is_empty():
        popped = s.pop()
        reverse_stack(s)
        insert_at_bottom(s, popped)
 
 
s = Stack()
data_list = input('Please enter the elements to push: ').split()
for data in data_list:
    s.push(int(data))
 
print('The stack:')
s.display()
reverse_stack(s)
print('After reversing:')
s.display()

problem-10:

class MinStack(object):
   min=float('inf')
   def __init__(self):
      self.min=float('inf')
      self.stack = []
   def push(self, x):
      if x<=self.min:
         self.stack.append(self.min)
         self.min = x
      self.stack.append(x)
   def pop(self):
      t = self.stack[-1]
      self.stack.pop()
      if self.min == t:
         self.min = self.stack[-1]
         self.stack.pop()
   def top(self):
      return self.stack[-1]
   def getMin(self):
      return self.min
m = MinStack()
m.push(-2)
m.push(0)
m.push(-3)
print(m.getMin())
m.pop()
print(m.top())
print(m.getMin())




  
