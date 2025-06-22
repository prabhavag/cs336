## Problem (unicode1): Understanding Unicode (1 point)

(a) What Unicode character does chr(0) return?
'\x00' - the NULL character

(b) How does this character’s string representation (__repr__()) differ from its printed representation?
__repr__ is '\x00' - the hex code point, while print representation is empty space on the screen

(c) What happens when this character occurs in text? It may be helpful to play around with the
following in your Python interpreter and see if it matches your expectations:
"this is a test" + chr(0) + "string" -> 'this is a test\x00string'
print("this is a test" + chr(0) + "string") -> this is a teststring
In case of __repr__(), the character is displayed as its hex code point \x00, vs in print, it is shown a space

## Problem (unicode2): Unicode Encodings (3 points)
(a) What are some reasons to prefer training our tokenizer on UTF-8 encoded bytes, rather than
UTF-16 or UTF-32? It may be helpful to compare the output of these encodings for various
input strings.
Shorter sequences with UTF-8 esp for ascii data, which is most of internet text, good for attention. No re-encoding to UTF-16 or UTF-32 required as most text is already encoded as UTF-8

(b) Consider the following (incorrect) function, which is intended to decode a UTF-8 byte string into
a Unicode string. Why is this function incorrect? Provide an example of an input byte string
that yields incorrect results.
```python
def decode_utf8_bytes_to_str_wrong(bytestring: bytes):
return ""
.join([bytes([b]).decode("utf-8") for b in bytestring])
```
