Given a string S, the task is to print all the duplicate characters with their occurrences in the given string.

Example:

Input: S = “geeksforgeeks”
Output:
e, count = 4
g, count = 2
k, count = 2
s, count = 2

**Solution**
```
def printDuplicates(str):
    # Converting string to list of characters
    char_list = list(str)
    # Sorting the list of characters
    char_list.sort()
    
    # Loop through the sorted list to find duplicates
    i = 0
    while i < len(char_list):
        count = 1
        # Counting the occurrences of each character
        while i < len(char_list)-1 and char_list[i] == char_list[i+1]:
            count += 1
            i += 1
        
        # Printing the duplicate character and its count
        if count > 1:
            print(char_list[i], ", count = ", count)
        i += 1

str = "test string"
printDuplicates(str)

```
