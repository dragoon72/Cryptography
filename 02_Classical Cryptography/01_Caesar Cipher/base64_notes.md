# Base64 Encoding Notes

## What is Base64?

Base64 is an **encoding technique** used to convert binary data into printable ASCII characters.

It is **NOT encryption**.

Anyone can easily decode Base64 encoded data.

---

# Why Base64 Exists

Computers store data in binary form:

```binary
01010101
```

Some systems can only safely handle printable text characters.

Base64 converts binary data into readable text so it can be:
- transmitted safely
- stored in text formats
- embedded in files/emails/URLs

---

# Base64 Character Set

Base64 uses 64 characters:

```text
A-Z
a-z
0-9
+
/
```

Total:

```text
26 + 26 + 10 + 2 = 64
```

That is why it is called **Base64**.

---

# Core Idea

Normal text uses:

```text
8-bit groups
```

Base64 uses:

```text
6-bit groups
```

Why 6 bits?

```text
2^6 = 64
```

So each 6-bit value maps to one Base64 character.

---

# Example

Character:

```text
M
```

ASCII binary:

```binary
01001101
```

Split into 6-bit groups:

```binary
010011 01
```

Padding bits are added:

```binary
010011 010000
```

Convert each group:

| Binary | Decimal | Base64 Character |
|--------|----------|------------------|
| 010011 | 19 | T |
| 010000 | 16 | Q |

Result:

```text
TQ
```

Padding is added:

```text
TQ==
```

Final Base64 output:

```text
TQ==
```

---

# Meaning of "="

Base64 works using:

```text
3 bytes = 24 bits
```

These become:

```text
4 Base64 characters
```

If input length is not divisible by 3, padding is needed.

Examples:

| Input | Base64 |
|-------|---------|
| M | TQ== |
| Ma | TWE= |
| Man | TWFu |

So:
- `=` means padding
- `==` means more padding

Some Base64 strings may not contain `=` if no padding is needed.

---

# Base64 is NOT Encryption

Base64 does NOT:
- use a secret key
- protect data
- provide security

It only changes representation.

Example:

```bash
echo "aGVsbG8=" | base64 -d
```

Output:

```text
hello
```

Anyone can decode it easily.

---

# Base64 in CTFs

CTF creators often hide flags using Base64.

Original flag:

```text
picoCTF{example_flag}
```

Encoded:

```text
cGljb0NURntleGFtcGxlX2ZsYWd9
```

Now searching with:

```bash
grep "picoCTF"
```

will fail because the visible text changed.

You must decode the Base64 string.

---

# How to Recognize Base64

Common signs:

## 1. Uses only Base64 characters

```text
A-Z a-z 0-9 + /
```

Sometimes:
- `-` replaces `+`
- `_` replaces `/`

(URL-safe Base64)

---

## 2. Ends with "=" or "=="

Example:

```text
SGVsbG8=
```

---

## 3. Looks random but readable

Example:

```text
YWRtaW46cGFzc3dvcmQ=
```

Decoded:

```text
admin:password
```

---

# Useful Commands

## Encode

```bash
echo "hello" | base64
```

## Decode

```bash
echo "aGVsbG8=" | base64 -d
```

---

# Important Comparison

| Technique | Purpose | Reversible | Secure |
|-----------|----------|-------------|---------|
| Base64 | Encoding | Yes | No |
| Hashing | Integrity / Password Storage | Usually No | Depends |
| Encryption | Security | Yes (with key) | Yes |

---

# Final Summary

Base64:

```text
binary data
→ split into 6-bit groups
→ map each group to one of 64 printable characters
```

It is:
- an encoding method
- reversible
- not secure
- commonly used in networking, emails, APIs, and CTFs
