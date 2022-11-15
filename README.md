# Attack Many Time Pad

## Approach

> Many time pad decrypt is all about guessing.

We will guess each character of plaintext

### Steps

Step 1: Guess the first character of the target plaintext. 
It might be the hardest since we have no clue on this char. 
But there is no choice so we must choose any random charater.

Step 2.a: For each guessed character, we will have the corresponding character 
of every ciphertexts. If any ciphertext has a meaningless word, we can guess 
another character by selecting `n` option. Otherwise, select `y` if you happy 
with that choice, and keep guessing.


Step 2.b: Correctly guess the next character of target ciphertext is good. But 
sometimes life is not that easy, and we can not think of any new possible words.
But 'When one door closes, another opens' (Graham Bell), and you found next 
character of other plaintext (not the target one). All you need to do is to 
select `h` option to choose the next character of that plaintext, and we can 
recalculate to suggest the next character you need to select in the in target 
ciphertext.

### How

How can we get the next character of other plaintexts on having guessed next 
character of target plaintext:
```
ciphertext_1 = plaintext_1 XOR key
ciphertext_2 = plaintext_2 XOR key

# XOR 2 ciphertexts together, we will have the same result on XOR-ing 2 plaintexts
xor_result_1 = ciphertext_1 XOR ciphertext_2
assert xor_result_1 == plaintext_1 XOR plaintext

# So if we know one plaintext (the guessed target one), we can know the other using
xor_result_2 = xor_result_1 XOR plaintext_1
assert xor_result_2 == plaintext_2
```

This technique is applied for both step 2.a and 2.b.

### Thanks for reading! 