# Caesar Cipher

## Overview

The Caesar Cipher is one of the oldest and simplest substitution ciphers.

It works by shifting each alphabet letter by a fixed number of positions.

Example:

```text
Plaintext : HELLO
Shift     : 3
Ciphertext: KHOOR
```

---

## Terminology

| Term | Meaning |
|--------|----------|
| Plaintext | Original readable message |
| Ciphertext | Encrypted message |
| Key | Shift value |
| Encryption | Converting plaintext to ciphertext |
| Decryption | Converting ciphertext back to plaintext |
| Brute Force | Trying every possible key |

---

## Encryption Process

Each letter is shifted forward.

Example:

```text
A → D
B → E
C → F
...
X → A
Y → B
Z → C
```

Shift value:

```text
Key = 3
```

---

## Mathematical Formula

Encryption:

```text
C = (P + K) mod 26
```

Where:

```text
C = Cipher letter
P = Plain letter
K = Shift key
```

Decryption:

```text
P = (C − K) mod 26
```

---

## Example

Plaintext:

```text
HELLO
```

Convert into alphabet positions:

```text
H = 7
E = 4
L = 11
L = 11
O = 14
```

Apply shift:

```text
7+3=10
4+3=7
11+3=14
11+3=14
14+3=17
```

Convert back:

```text
K
H
O
O
R
```

Result:

```text
KHOOR
```

---

# C++ Encryption Script

```cpp
#include<iostream>
#include<string>
using namespace std;

int main()
{
    string text;

    cout<<"Enter text: ";
    getline(cin,text);

    int shift;

    cout<<"Enter shift: ";
    cin>>shift;

    string result="";

    for(char ch:text)
    {
        if(isalpha(ch))
        {
            ch=toupper(ch);

            char newChar=
            ((ch-'A'+shift)%26)
            +'A';

            result+=newChar;
        }
        else
        {
            result+=ch;
        }
    }

    cout<<"Encrypted: "<<result;

    return 0;
}
```

---

# C++ Automatic Brute Force Script

Purpose:

Try all possible shifts automatically.

```cpp
#include<iostream>
#include<string>
#include<cctype>

using namespace std;

int main()
{
    string cipher;

    cout<<"Enter cipher text:";
    getline(cin,cipher);

    for(int shift=0;shift<26;shift++)
    {
        string result="";

        for(char ch:cipher)
        {
            if(isalpha(ch))
            {
                ch=toupper(ch);

                char newChar=
                ((ch-'A'-shift+26)%26)
                +'A';

                result+=newChar;
            }
            else
            {
                result+=ch;
            }
        }

        cout<<"Shift "
            <<shift
            <<" : "
            <<result
            <<endl;
    }

    return 0;
}
```

---

## Example Output

Input:

```text
KHOOR
```

Output:

```text
Shift 0 : KHOOR
Shift 1 : JGNNQ
Shift 2 : IFMMP
Shift 3 : HELLO
```

---

## Cryptanalysis

Caesar Cipher is weak because only:

```text
26 possible keys
```

exist.

Attack methods:

- Brute Force
- Frequency Analysis
- Known Plaintext Attack

---

## Time Complexity Analysis

Outer Loop:

```text
26
```

Inner Loop:

```text
N
```

Total:

```text
O(26 × N)
```

Simplified:

```text
O(N)
```

Reason:

26 is a constant.

---

## Important Notes

- Caesar cipher preserves letter frequency
- Modern cryptography does not use Caesar cipher
- Caesar cipher is useful for learning cryptographic fundamentals
- ROT13 is a special Caesar cipher using shift = 13

---

## Future Topics

- [ ] Frequency Analysis
- [ ] Monoalphabetic Substitution
- [ ] Vigenère Cipher
- [ ] Playfair Cipher
- [ ] Rail Fence Cipher
- [ ] Columnar Transposition
- [ ] One Time Pad
- [ ] Python Implementation
- [ ] Caesar Cracker using Frequency Analysis

---

## Personal Notes

Add observations here.

```
Brute force does not always return the final answer.

It returns candidate plaintexts.

The analyst must:

1. Identify meaningful text
2. Detect partial decryption
3. Check for additional cipher layers
```
[example](https://learn.cylabacademy.org/learning-paths/17/133?workspace=true)
```text
here in this example we have to look for the meaningfull decrypted texts and check whether its partially or fully readable.If none of the shifts make it fully legible then we take the one with the closest meaningfull text and then again bruteforce it for the other half
```
