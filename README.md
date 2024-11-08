# esoteric-hello-world-v2
This is esoteric "hello world" program (Version 2) made in Python3.
The first version of this program is [Esoteric python hello world](https://github.com/VelikiFeniks0/esoteric-python-hello-world) and version 2 works on the same principle.

It imports `os` module, uses write method, and this time instead of having a list of ASCII characters, it is a list of ordinal numbers of ASCII characters, for example "h" in ASCII table is 104.

In this code we do not have lots of booleans, instead we have lambda arguments.
Like this:
```py
(lambda arg1, arg2:
  ...
)(True, False)
```
It looks cleaner than spamming lots of booleans.

Remember that list of ASCII ordinal numbers I mentioned earlier?
It's just a list that has ordinal numbers for each character in string "hello world".
```py
l = [104, 101, 108, 108, 111, 32, 119, 111, 114, 108, 100] # hello world
```
We have to obfuscate it more so we just use booleans to act as numbers. True is equal to 1 and False is equal to 0, but how do we get larger numbers such as 104?
We can use bitwise operators and bit shifting. 
Bit shifting in Python works in a way where you write a number, write a bitwise operator for bit shifting and another number.
There are two bitwise operators for bit shifting in Python, which are left shift [`<<`] and right shift [`>>`].

## How bit shifting works?
Let's say, you have a number 2, which in binary is 10.
If you left shift it by one, you'll get 4 in binary.

`2 << 1 -> 4`

Because in binary, you move 10 (number 2) by one bit, and it becomes 100 (4 in binary). You move that 10 to left.
Same thing for right shift.

`7 >> 1 -> 3`

7 in binary is 111 and 3 in binary is 11, and you move 111 by one bit to the right.

That's how you can get larger or smaller numbers with bit shifting.

## The code
Here's the obfuscated version of a list of ASCII ordinal numbers.
```py
_=bool(-~([]>[]));__=False;___=[((((_<<(_^__))**(_<<(_&_//(_^__//_))<<_))*(_<<_<<_<<_))-(_<<(_//_^__)<<_<<(_//_^__//_)<<_<<_)+(_<<(_//_^__)<<_<<_)),
    ((((_<<_)**(_<<_<<_))*(_<<_<<_<<_))-(_<<_<<_<<_<<_<<_)+(_<<_<<_<<_)-(_<<_<<_)+(_^__%_)),
    ((((_<<(_^__))**(_<<(_&_//(_^__//_))<<_))*(_<<_<<_<<_))-(_<<(_//_^__)<<_<<(_//_^__//_)<<_<<_)+(_<<(_//_^__)<<_<<_)+(_<<_<<_)),
    ((((_<<(_^__))**(_<<(_&_//(_^__//_))<<_))*(_<<_<<_<<_))-(_<<(_//_^__)<<_<<(_//_^__//_)<<_<<_)+(_<<(_//_^__)<<_<<_)+(_<<_<<_)),
    ((((_<<(_^__))**(_<<(_&_//(_^__//_))<<_))*(_<<_<<_<<_))-(_<<(_//_^__)<<_<<(_//_^__//_)<<_<<_)+(_<<(_//_^__)<<_<<_)+(_<<_<<_)+(_<<_)+(__^_&_)),
    (_<<_<<_<<_<<(_&(_+(_<<_))&_)<<(_^__//_)),
    ((((_<<(_^__))**(_<<(_&_//(_^__//_))<<_))*(_<<_<<_<<_))-(_<<(_//_^__)<<_<<(_//_^__//_)<<_<<_)+(_<<(_//_^__)<<_<<_)+(_<<_<<_)+(_<<_)+(__^_&_)+(_<<_<<_<<_)),
    ((((_<<(_^__))**(_<<(_&_//(_^__//_))<<_))*(_<<_<<_<<_))-(_<<(_//_^__)<<_<<(_//_^__//_)<<_<<_)+(_<<(_//_^__)<<_<<_)+(_<<_<<_)+(_<<_)+(__^_&_)),
    ((((_<<(_^__))**(_<<(_&_//(_^__//_))<<_))*(_<<_<<_<<_))-(_<<(_//_^__)<<_<<(_//_^__//_)<<_<<_)+(_<<(_//_^__)<<_<<_)+(_<<_<<_)+(_<<_)+(__^_&_)+(_<<_<<_)-_),
    ((((_<<(_^__))**(_<<(_&_//(_^__//_))<<_))*(_<<_<<_<<_))-(_<<(_//_^__)<<_<<(_//_^__//_)<<_<<_)+(_<<(_//_^__)<<_<<_)+(_<<_<<_)),
    (((((_<<(_^__))**(_<<(_&_//(_^__//_))<<_))*(_<<_<<_<<_))-(_<<(_//_^__)<<_<<(_//_^__//_)<<_<<_)+(_<<(_//_^__)<<_<<_)+(_<<_<<_)+(_<<_)+(__^_&_)+(_<<_<<_)+_)-(_<<_<<_<<_<<_))]
```
I know it looks messy and complicated, but trust me, it's not that complicated. First what we have is two weird variables called `_` and `__` and a list of ASCII ordinal numbers, it's all in one line. Those first two variables are basically just one True and one False value, The first variable has some weird, but small code in it, it's literally just some random stuff that returns `True` as an output, so we have bool type and inside we see `-~([]>[])`. `[]>[]` returns `False` as an output because first list is not larger than the second one, they are equally empty, `-~` is there because when you use `~` bitwise operator that stands for NOT bitwise operator, since []>[] is False, bitwise NOT should make it the opposite from False and become True, but there's a sequence, it does not result in `True`, instead it displays `-1` and then we add `-` in front of bitwise NOT (~) to make it a 1. But 1 is not a boolean type (`True`), in that situation we just use `bool()` to make it a bool type and not an integer.

That list looks complicated, but every element is just a number that we got by bit shifting numbers, there are many other bitwise operator, but they are there just to make it more obfuscated and confusing. The first two variables are mentioned here in the elements of the list many times, but those are just booleans, True and False. Those bitwise operators like `^` and `&` are just to make it more confusing, `^` is XOR, and `&` is AND. XOR means if only one of the inputs is true, then the output is also true, AND means if both inputs are true, then the output is also true, otherwise it's not true on the output.

Now we want to print all those characters, we can simply use `print` function, but that's not esoteric nor obfuscated. We have to obfuscate it more. `os˙ module is a great way to output some text on terminal, it's the lowest-level way to output text in Python.

To do that, we have to write this simple chunk of code:
```py
import os
os.write(1, b"hello world")
```
As you can see, `os.write` requires two arguments, a file decriptor, and bytes-like object, which in this case is a "hello world" string, but encoded.
File decriptor has to be 1 in this code, but in general it represents the target file where the bytes will be written, and yes, the string has to be bytes-like object.

We could obfuscate it a little more and use `getattr` function and maybe some anonymous functions (lambdas).

getattr example:
```py
getattr(
  __import__("os"), "write"
)(1, b"hello world")
```
