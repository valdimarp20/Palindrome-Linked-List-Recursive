## Approach: Reverse list and compare original
```Python
def reverse_list(head, reverse=None):

    # If we reach the tail or if the list is empty
    if head is None:
        return reverse

    # New node with head data from call stack
    reverse = Node(head.data, reverse)
    return reverse_list(head.next, reverse)

def palindrome_compare(head, reversed_head):

    # All values have been compared
    if head is None:
        return True

    # If reversed data is same head data
    # Continue comparing
    if head.data == reversed_head.data:
        return palindrome_compare(head.next, reversed_head.next)

    return False
    
def palindrome(head):

    # Create a temporary reversed head
    reverse_head = reverse_list(head)

    # Compare reversed with original head
    return palindrome_compare(head, reverse_head)
```
#### Complexity Analysis
* Time Complexity: O(n), best & worst case
* Space Complexity: O(n)
* Reverse_list, time Complexity: O(n)

## Approach: One recursive function & one recursive call 
```Python
class Node:
    def __init__(self, data=None, next=None):
        self.data = data
        self.next = next

def palindrome_compare(front, head):

    # List is empty
    if head is None:
        return front

    # Call until we reach end of the list.
    palindrome_compare(front, head.next)

    # The first pop from call stack will not run this
    if front.data == False:
        return front

    # Compare front with the back(reversed head from call stack)
    # True if front same as back, else False
    front.data = head.data == front.next.data
    front.next = front.next.next

    return front
    
def palindrome(head):

    # Create a new node pointing to head
    front = Node(True, head)

    # Data of the return node tells us if list is palindrome
    return palindrome_compare(front, head).data

```
#### Complexity Analysis
* Time Complexity: O(n)
* Space Complexity: O(n). 
