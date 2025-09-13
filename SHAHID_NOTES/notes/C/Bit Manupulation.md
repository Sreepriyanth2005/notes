
#### AND

##### 1. Masking bits → Keep only specific bits
```c
#include <stdio.h>

int main() {
    int n = 0x1234;       // 0x1234 = 0001 0010 0011 0100 (binary)
    int masked = n & 0xFF; // Keep only last 8 bits (0x34)
    
    printf("Masked value: 0x%X\n", masked);
    return 0;
}

op:
Masked value: 0x34
```

##### 2 . Check if a bit is set (set = 1)
```c
#include <stdio.h>

int main() {
    int n = 42;         // 42 = 101010 (binary)
    int k = 3;          // Check 3rd bit (0-based from right)
    
    if (n & (1 << k))
        printf("Bit %d is set\n", k);
    else
        printf("Bit %d is not set\n", k);
    
    return 0;
}
op:
Bit 3 is set
```

##### 3. Clear specific bits
```c
#include <stdio.h>

int main() {
    int n = 15;          // 1111 (binary)
    int mask = 1 << 2;   // Clear 2nd bit (value 4)
    
    int result = n & ~mask;
    printf("After clearing bit 2: %d\n", result);
    
    return 0;
}
op:
After clearing bit 2: 11  (binary 1011)
```

##### 4 . Check if number is even
```c
#include <stdio.h>

int main() {
    int n = 42;
    
    if ((n & 1) == 0)
        printf("%d is even\n", n);
    else
        printf("%d is odd\n", n);
    
    return 0;
}
```

##### 5 . Modulo power of 2 (** only works when the divisor is a power of 2 **)

```c
#include <stdio.h>

int main() {
    int n = 77;
    int k = 4;                // 2^4 = 16
    int mod = n & ( (1 << k) - 1 ); 
    
    printf("%d %% %d = %d\n", n, (1<<k), mod);
    return 0;
}

op:
77 % 16 = 13
```
---
### OR

##### 1 . Set a Specific Bit
```c
#include <stdio.h>

int main() {
    int n = 42;          // 42 = 101010 (binary)
    int k = 1;           // Set 1st bit (0-based from right)

    int result = n | (1 << k); // Forces that bit to 1
    printf("After setting bit %d: %d\n", k, result);

    return 0;
}
op:
After setting bit 1: 42
```

##### 2 . Union of Sets (Using Bit Masking)

```c
#include <stdio.h>

int main() {
    int setA = 0b10101;  // {0,2,4}
    int setB = 0b00111;  // {0,1,2}

    int unionSet = setA | setB;

    printf("Union: %d (binary %05b)\n", unionSet, unionSet);
    return 0;
}
op:
Union: 23 (binary 10111)
```

##### 3. Force Certain Bits to 1 With a Mask

```c
#include <stdio.h>

int main() {
    int n = 0b100100;   // 36
    int mask = 0b001011;// force bits 0,1,3 to 1

    int result = n | mask;
    printf("After forcing bits: %d (binary %06b)\n", result, result);
    return 0;
}
op:
After forcing bits: 47 (binary 101111)
```

---
### XOR

##### 1. Toggle (Flip) a Bit
```c
#include <stdio.h>

int main() {
    int n = 42;      // 101010
    int k = 1;       // Toggle 1st bit (0-based)

    int result = n ^ (1 << k);
    printf("After toggling bit %d: %d\n", k, result);

    return 0;
}
op:
After toggling bit 1: 40
```

##### 2. **Find Differing Bits Between Numbers**

```c
#include <stdio.h>

int main() {
    int a = 6;  // 110
    int b = 3;  // 011

    int diff = a ^ b;
    printf("Differing bits: %d (binary %03b)\n", diff, diff);

    return 0;
}
op:
Differing bits: 5 (binary 101)
```

##### 3 . Swap Two Numbers Without Temp
```c
#include <stdio.h>

int main() {
    int a = 5, b = 9;

    a = a ^ b;
    b = a ^ b;
    a = a ^ b;

    printf("After swap: a=%d, b=%d\n", a, b);
    return 0;
}
op:
After swap: a=9, b=5
```

##### 4 . Find Unique Element in Array
```c
#include <stdio.h>

int main() {
    int arr[] = {2, 3, 2, 4, 4};
    int n = 5;
    int unique = 0;

    for(int i = 0; i < n; i++)
        unique ^= arr[i];

    printf("Unique element: %d\n", unique);
    return 0;
}
op:
Unique element: 3
```

##### 5. XOR-Based Encryption/Decryption
```c
#include <stdio.h>

int main() {
    char msg = 'A';  // 65
    char key = 23;

    char encrypted = msg ^ key;
    char decrypted = encrypted ^ key;

    printf("Encrypted: %d, Decrypted: %c\n", encrypted, decrypted);
    return 0;
}
op:
Encrypted: 86, Decrypted: A
```

##### 6 . Detect if Two Numbers are Different

```c
#include <stdio.h>

int main() {
    int a = 10, b = 12;

    if (a ^ b)
        printf("Numbers are different\n");
    else
        printf("Numbers are same\n");

    return 0;
}
op:
Numbers are different
```

---

### Left Shift (n * 2 ^ s)

##### 1. Fast Multiply by Powers of 2

```c
#include <stdio.h>

int main() {
    int n = 7;
    int k = 3;               // Multiply by 2^3 = 8

    int result = n << k;     // 7 * 8 = 56
    printf("%d << %d = %d\n", n, k, result);

    return 0;
}
op:
7 << 3 = 56
```

##### 2 . Move a Bit to a Specific Position
```c
#include <stdio.h>

int main() {
    int k = 5;        // Move to 5th position (0-based)
    int bitMask = 1 << k;

    printf("1 << %d = %d (binary mask)\n", k, bitMask);
    return 0;
}
op:
1 << 5 = 32 (binary mask)
```

##### 3 . Encode Multiple Values into a Single Int (Bit-Packing)

```c
#include <stdio.h>

int main() {
    int x = 9;  // 1001
    int y = 6;  // 0110

    int packed = (x << 4) | y;   // Move x to high 4 bits
    printf("Packed: %d (binary)\n", packed);

    int unpackX = packed >> 4;
    int unpackY = packed & 0xF;  // last 4 bits

    printf("Unpacked: x=%d, y=%d\n", unpackX, unpackY);
    return 0;
}
op:
Packed: 150 (binary)
Unpacked: x=9, y=6
```

##### 4 . Create Powers of 2 Quickly
```c
#include <stdio.h>

int main() {
    for (int k = 0; k < 5; k++)
        printf("2^%d = %d\n", k, 1 << k);
    return 0;
}
```
---

### Right Shift(n / 2 ^ s)

##### 1 . Fast Divide by Powers of 2

```c
#include <stdio.h>

int main() {
    int n = 100;
    int k = 3;           // Divide by 2^3 = 8

    int result = n >> k; // 100 / 8 = 12
    printf("%d >> %d = %d\n", n, k, result);

    return 0;
}
op:
100 >> 3 = 12
```

##### 2 . Extract a Specific Bit
```c
#include <stdio.h>

int main() {
    int n = 42;      // 101010
    int k = 3;       // 0-based from right

    int kthBit = (n >> k) & 1;
    printf("Bit %d of %d = %d\n", k, n, kthBit);

    return 0;
}
op:
Bit 3 of 42 = 1
```

##### 3 . Check if a Number is Power of 2 by Reducing to 1
```c
#include <stdio.h>

int main() {
    int n = 16;   // check if power of 2
    int temp = n;

    while (temp > 1) {
        if (temp & 1) { // If any 1 appears in lower bits before reaching 1
            printf("%d is NOT a power of 2\n", n);
            return 0;
        }
        temp >>= 1;
    }

    printf("%d is a power of 2\n", n);
    return 0;
}
op:
16 is a power of 2
```
##### 4 . Floor Division for Powers of 2
```c
#include <stdio.h>

int main() {
    int n = 19;

    int divBy2 = n >> 1;  // 19 / 2 = 9
    int divBy4 = n >> 2;  // 19 / 4 = 4
    int divBy8 = n >> 3;  // 19 / 8 = 2

    printf("19>>1=%d, 19>>2=%d, 19>>3=%d\n", divBy2, divBy4, divBy8);
    return 0;
}
op:
19>>1=9, 19>>2=4, 19>>3=2
```

-------


### General 

##### 1 . Count no of bits in a number 
```c
// Online C compiler to run C program online
#include <stdio.h>

int main() {
    
    int digit = 17; //10001
    int count = 0;
    while(digit > 0){
        count++;
        digit>>=1;
    }
    printf("%d",count);
    return 0;
}
```

##### 2 . Count no of set bit (Brian Kernighan’s Algorithm)
```c
while(digit > 0) {
    digit = digit & (digit - 1);  // remove the rightmost 1-bit
    count++;
}
```

##### 3 .  Count no of Unset bit
```c
#include <stdio.h>
int main() {
    int num = 17;
    int count = 0;

    while(num > 0) {
        if((num & 1) == 0)  // Check if the last bit is 0
            count++;
        num >>= 1;          // Shift right
    }

    printf("Unset bits: %d\n", count);
    return 0;
}
```

##### 4 . Swap two numbers without variable

```
a = a ^ b
b = a ^ b  
a = a ^ b
```

##### 5 . Addition 
```c
int bitwiseAdd(int a, int b) {
    while (b != 0) {
        int carry = a & b;    // Calculate carry
        a = a ^ b;            // Sum without carry
        b = carry << 1;       // Move carry to next position
    }
    return a;
}
```

##### 6  . Subtraction
```c
int bitwiseSubtract(int a, int b) {
    return bitwiseAdd(a, bitwiseAdd(~b, 1));  // a + (-b)
}
```