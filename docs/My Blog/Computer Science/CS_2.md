# CS_2: Why do we use the ending character `/0`

*Created: April 21, 2024*

In [CS_1](CS_1.md), we answered the question of why in most programming languages, the index of a list or an array starts from 0, not 1. However, one unanswered question was why do we have to use the `\0` character to mark the end of the array, and not just caching the address of the actual last element?

The reason lies in the bits and bytes. Basic information: a ***bit*** can be 0 or 1, and a ***byte*** is a group of 8 bits. Each byte in the computer memory will have a different address.

Something like an `int` will take up 4 bytes, and the address of the first byte is the address of the `int` element. Imagine an `int` array like this:

```
{element_1, element_2, element_3, ... <byte_1><byte_2><byte_3><byte_4>}
```

The address of the first element is the start of the array, yes, but the address of the last element is not the end of the array! It is, in fact, 3 bytes short. That is why the C compiler automatically add `\0` at the end of the array, and identifies the array as the start to before the end character.

By the way, if you ask why the C compiler knows where to add the end character, it is because you are forced to declare all elements or the number of elements in the array definition.