# CS_1: The start of an array

*Created: April 19, 2024*

*Last modified: April 21, 2024*

Ever wonder why an array (or a list, for Python pals), starts at 0? Throughout my first and second year, this question had not been on the back of my mind. Until one day, something clicked.

It involves something called the ***pointer***. You might have heard of it if you have used a low-level language like C. Basically, it is a variable that stores a memory address. The computer can then use that address and retrieve data.

An array, as intuitive as it can be, is stored as consecutive segments of memory. Now, with that information, imagine yourself as the computer, what would you need to know to be able to work your way through an array?

1. **Is it an array?** You cannot just assume that the computer knows what you are refering to is an array. You have to tell it.
2. **Where does the array start?** It starts with a specific element, and the first byte that element has an address. This can be stored in a pointer!
3. **Where does the array end?** It ends with an element, but instead of storing the address of that element, we add an element after that ending element. That final element is an end character, or `\0`. If you wonder why can't we store the address of the ending element, please see [CS_2](CS_2.md) post.
4. **How big is each element?** You have to tell the computer that this is an array of `int`, or `double`. Usually `int` is 4 bytes, `double` is 8.

Let us look at the following example:

```c
int c[] = {2, 1, 4, 5}; 
```

We are explicitly tell the computer that:

- This is an array (by using the syntax `c[]`).

- This is an array of `int`. All elements are 4 bytes each.

- We are using the pointer variable `c` to identify the starting address of the array!

- Although not shown, but the compiler secretely added a `\0` character to mark the end. The actual array in memory is `{2, 1, 4, 5, \0}`.

With such information, to traverse to whole array, we only need to leap 4 bytes many times, starting from the address stored in `c`, and ending when we reach the `\0` character.

Back to the main question, the index of an array starts from 0? Well, it shows the number of times that we have to leap, from the start, to reach the target element. In other words, it is the distance from the starting point. First element will be 0 element away from the start, isn't it?

Can we just know how it works internally, and create a language where we index the first element as 1? Yes, absolutely. Prime examples are Pascal and Julia. However, the choice of indexing from 0 is more popular, and the only reason I could think of is that in the majority of cases it is better to look at things like a computer. Pascal on the other hand, is made to be simple, and Julia is made for mathemeticians who want to write code that looks as much like their research paper as possible, rather than programming.