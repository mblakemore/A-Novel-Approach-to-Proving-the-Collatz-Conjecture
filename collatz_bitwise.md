## The Collatz Conjecture - Bitwise

### Collatz Function Bitwise Operations

1. **Even Numbers:**
   - For an even number ( n ), ( C(n) = frac{n}{2} ). In binary, this operation is equivalent to a right shift by one bit.
   - For example, if ( n = 8 ) (which is ( 1000_2 ) in binary), then ( C(n) = 4 ) (which is ( 0100_2 )).

   ```
   C(n) = n >> 1
   ```

2. **Odd Numbers:**
   - For an odd number ( n ), ( C(n) = 3n + 1 ). This can be broken down into bitwise operations:
     - Multiplying ( n ) by 3 can be achieved by ( (n << 1) + n ).
     - Adding 1 to the result is straightforward.

   ```
   C(n) = (n << 1) + n + 1
   ```

### The Collatz sequence using registers and bitwise operations:

```
def collatz_sequence(n):
    while n != 1:
        if n & 1 == 0:  # If n is even
            n = n >> 1
        else:           # If n is odd
            n = (n << 1) + n + 1
    return n
```

### Registers

1. **Initial State:**
   - Start with a positive integer ( n ) stored in a register.

2. **Even Case (Right Shift):**
   - If the least significant bit (LSB) is 0 (indicating ( n ) is even), perform a right shift operation.

3. **Odd Case (Shift and Add):**
   - If the LSB is 1 (indicating ( n ) is odd), perform a left shift by 1 bit, add the original number to the result, and then add 1.

### Example: ( n = 7 )

1. ( n = 7 ) (( 111_2 ))
   - Odd, so ( C(7) = (7 << 1) + 7 + 1 = 14 + 7 + 1 = 22 )

2. ( n = 22 ) (( 10110_2 ))
   - Even, so ( C(22) = 22 >> 1 = 11 )

3. ( n = 11 ) (( 1011_2 ))
   - Odd, so ( C(11) = (11 << 1) + 11 + 1 = 22 + 11 + 1 = 34 )

4. ( n = 34 ) (( 100010_2 ))
   - Even, so ( C(34) = 34 >> 1 = 17 )

5. ( n = 17 ) (( 10001_2 ))
   - Odd, so ( C(17) = (17 << 1) + 17 + 1 = 34 + 17 + 1 = 52 )

6. ( n = 52 ) (( 110100_2 ))
   - Even, so ( C(52) = 52 >> 1 = 26 )

7. ( n = 26 ) (( 11010_2 ))
   - Even, so ( C(26) = 26 >> 1 = 13 )

8. ( n = 13 ) (( 1101_2 ))
   - Odd, so ( C(13) = (13 << 1) + 13 + 1 = 26 + 13 + 1 = 40 )

9. ( n = 40 ) (( 101000_2 ))
   - Even, so ( C(40) = 40 >> 1 = 20 )

10. ( n = 20 ) (( 10100_2 ))
    - Even, so ( C(20) = 20 >> 1 = 10 )

11. ( n = 10 ) (( 1010_2 ))
    - Even, so ( C(10) = 10 >> 1 = 5 )

12. ( n = 5 ) (( 101_2 ))
    - Odd, so ( C(5) = (5 << 1) + 5 + 1 = 10 + 5 + 1 = 16 )

13. ( n = 16 ) (( 10000_2 ))
    - Even, so ( C(16) = 16 >> 1 = 8 )

14. ( n = 8 ) (( 1000_2 ))
    - Even, so ( C(8) = 8 >> 1 = 4 )

15. ( n = 4 ) (( 100_2 ))
    - Even, so ( C(4) = 4 >> 1 = 2 )

16. ( n = 2 ) (( 10_2 ))
    - Even, so ( C(2) = 2 >> 1 = 1 )
