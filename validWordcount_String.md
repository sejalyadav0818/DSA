# Word counting and time/space complexity analysis:


# Simple Logic Using Regular Expressions and Iterative Approach

This file demonstrates two different methods for counting the number of words in a sentence using Python. The first method uses regular expressions, while the second method uses iteration with character checking.

## Method 1: Using Regular Expressions

In this approach, we use Python's `re.split()` function to split the sentence into words based on any sequence of whitespace or punctuation marks.

### Code:

```python
import re

# Take input from the user
sentence = input()

# Use a regular expression to split the sentence by any sequence of whitespace or punctuation
words = re.split(r'[ \t\n,;.!?]+', sentence.strip())  # Strip leading/trailing spaces
words = [word for word in words if word]  # Remove empty strings

# Count the number of words
count = len(words)
print(count)
```

### Explanation:
1. **Input:** The user inputs a sentence.
2. **Splitting:** The `re.split()` function splits the sentence by any sequence of whitespace or punctuation characters.
3. **Count:** The number of words is calculated by counting the length of the resulting list.

### Time and Space Complexity:
- **Time Complexity:** O(n), where `n` is the length of the sentence. We are iterating over the sentence once to split it.
- **Space Complexity:** O(m), where `m` is the number of words in the sentence. The space is used for storing the resulting list of words.

## Method 2: Iterative Word Counting

This method iterates through each character in the sentence, counting the number of words by detecting transitions from non-alphanumeric characters to alphanumeric characters.

### Code:

```python
import string

# Take input from the user
sentence = input()

# Initialize variables
count = 0
in_word = False  # To track if we're inside a word

# Iterate through each character in the sentence
for char in sentence:
    # Check if the character is a letter or digit (part of a word)
    if char.isalnum():  # Checks for letters and numbers
        if not in_word:
            count += 1  # Found the start of a new word
            in_word = True
    else:
        in_word = False  # Reset when encountering a space or punctuation

# Print the number of words
print(count)
```

### Explanation:
1. **Input:** The user inputs a sentence.
2. **Character Iteration:** The program checks each character to see if it's part of a word (alphanumeric). When it encounters the start of a word, it increments the word count.
3. **Count:** The number of words is calculated during the iteration.

### Time and Space Complexity:
- **Time Complexity:** O(n), where `n` is the length of the sentence. Each character is checked once.
- **Space Complexity:** O(1), as no extra space is used except for a few variables.

## Conclusion

Both methods provide efficient solutions for counting words in a sentence. The choice of method can depend on the context of the task—whether you prefer using regular expressions for simplicity or prefer a manual iteration approach for more control over word boundaries.
