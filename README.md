# Basic CS Interview Guide

## Introduction
### Topics
Technical interview questions come in a few categories. These include
* Fizz-buzz like questions to check if you're a minimally competent programmer
* Behavioral questions, both about previous experiences, and what actions you'd take in certain situations
* Hard-core technical design and coding questions involving algorithms and data structures

This guide will be primarily concerned with the latter two points, with heavy emphasis given to the last point. This guide assumes minimal competency with programming.

### Choice of Language
You should first and foremost choose a language used at the company. If the company uses multiple languages, the highest level language should be used. If there are multiple high level languages (such as Python, Ruby, and CoffeeScript), you should choose the one you are most comfortable in.

Applicants interviewing with higher-level languages tend to have greater success on average than those with lower-level languages. This is because with higher-level languages one needs to write less, there are fewer opportunities to introduce bugs, and it's often less mental effort. There are certainly exceptions; if you're interviewing to write device drivers, you had better exhibit proficiency with lower-level languages!

This guide will have code written in Python, as this is the language I am encouraging my friend to use (and happens to be my favorite interview language.) 

### Behavioral and social aspects
I won't speak a lot to this extremely important aspect of interviews simply because I don't think I'm very qualified to. With that said,
* Don't argue with and upset the interviewer. I've seen this happen. Not pretty.
* Act natural, confident, and look your interviewer in the eyes.
* Smile when appropriate, and treat your interviewer as you would a coworker.
* Don't panic or act nervous. This is not good. 
* When solving a problem, talk out loud. Whether you know exactly what to do, or have no idea what to do, the interviewer doesn't want to see your solution so much as they want to see your problem solving process.
* If you have seen an interview question before, tell the interviewer. This shows honesty.
* If you have no idea how to do a question, don't panic, and just start talking through it. Again, don't panic or get nervous, your job is not to solve the questions, it's to think through them.

The last point is extremely important. Often, interviewers will give you extremely hard questions which you have often no chance of solving. They know this, and do it to gauge how you work under pressure. Remember,
* Don't panic.
* Don't be nervous.
* Talk through the problem.
* Don't be afraid to ask for help if you're stuck.

### Behavioral questions
Of the questions companies ask, these are often the hardest. Some examples are 
* "What was the hardest bug you've encountered, and how did you fix it?"
* "Did you ever have disputes with your coworkers or boss? If so, about what, why, and how did you resolve them?"
\* The only way to prepare for these is to try and think of some potential classes of questions and have anecdotes relating to them. If you lack experience, don't say nothing or make something up. It's much better to tell the interviewer the truth; that you don't have a development experience which would give them a meaningful answer to their question.

### Purpose and Citation
The purpose of this guide is to help one of my friends prepare for an interview at Google. Much of the material I have read to produce this guide is from the University of Michigan EECS 281 slides produced by professors David Paoletti and  Don Windsor. I will never copy the material verbatim, but the organization of the guide may reflect the organization of the class. With that said, if anyone takes issue with the content of this guide, please contact me at michael@codecombat.com, and I will be happy to review your request and make edits if necessary.

## Technical Interview Questions
Many of the interview questions you'll experience fit into a few broad categories:
* Complexity analysis
* Choosing and implementing various algorithms
* Choosing and implementing various data structures
* Higher-level design questions
* General problem solving

I will touch on all of these, but focus on algorithms and data structures.

### Complexity Analysis
#### Why does this matter?
Runtime of a program is affected by a number of things, including how good the programmer is, how fast the computer running the program is, and how the program was compiled. At companies like Google, we can assume that the program implementation is close to optimal, that computer power is no issue, and that the compiler is excellent. So then what does affect the runtime of a program? Algorithms.

In a lot of projects, the choice of certain algorithms, like sorting, might not make a significant difference in the user's experience. Who cares if a sorting algorithm takes 1ms or 20ms? But this is not the case with Google.   
If you want to analyze tens of billions of emails, trillions of webpages, have cars drive themselves, or machines identify cat videos, algorithms _do_ matter. In fact, they matter a lot more than compilers, programmers, and CPU speed put together. Choice of algorithms might not make a difference a lot of situations, but with the interesting problems, they certainly do. Which is why Google certainly will ask you about them. And they'll most likely ask you to do complexity analysis.

#### How do you measure input size?
Number of items is the most common way to measure input size, but sometimes it's better to be more specific or less specific. For instance, if you have a graph, it's common to measure algorithmic complexity in terms of vertices and edges, and sometimes it's more common to measure algorithmic complexity in bits. Just use common sense with regard to the problem at hand.

#### Why don't we just measure steps done?
There are a few problems with conducting runtime measurements like this. The first is that due to differences in compilers and instruction set architectures, this is not a reliable count of the actual instructions run by the processor. Secondly, it's not trivial to count the number of cycles executed for a single, known input, much less every possible input. It's much more worthwhile to measure runtime growth in terms of input size; this is the essence of Big O notation.

#### Big O Notation
It's best if you already know the mathematical foundations of this. Just remember, saying an algorithm is O(n) is saying that, at the very most, the runtime grows proportionally to n. Note that an O(1) algorithm is also O(n). Likewise, big omega is a lower bound, and big theta is an asymptotically tight bound.

Some common complexity classes include
* O(1), or constant
* O(log n), or logarithmic
* O(n), or linear
* O(n log n), or loglinear
* O(n^2), or quadratic
* O(c^n), or exponential
* O(n!) or factorial
* O(2^2^n), or doubly exponential

Big O notation can measure best case, worst case, and average case of performance (based on input case.)   
Amortized complexity is a type of worst case complexity that can be considered an average complexity. For instance, with a phone card, you pay $20 up front, but you may be paying an average of 15 cents per minute. Likewise with the C++ STL vector, you may have O(1) complexity for the push back operation 99% of the time, but when it needs to expand, it takes log linear time. Even though this operation's worst case is log linear, we can say it's amortized O(1). 

### Pseudocode
Algorithms are often described in pseudocode, a language resembling Python code written when the author has a high blood alcohol level. 

### Recursion
Recursion is a handy tool for discovering new algorithms, as well as quick implementations of other algorithms. In reality, the performance of a recursive algorithm is often lower than its equivalent iterative version. Remember, **every recursive function can be converted to an iterative function with the use of a stack.**

Dafuq is a stack?

#### Stacks
A stack is a last in, first out(LIFO) data structure. It supports three operations: looking what value is on the top of a stack, popping the top value of a stack, and pushing a new value onto the top of the stack. This is commonly implemented as an STL vector(using the `myVec.push_back()`, `myVec.back()`, and `myVec.pop_back()` methods), or in Python, an array, with `myArray.append()`, `myArray.pop()`, and `myArray[-1]`. 

myStack = \[\]
myStack.append(5)
myStack.append(10)
print(myStack.pop()) #prints 10
print(myStack\[-1\]) #prints 5

There are awesome animations of data structures online. I don't have the link offhand, but I wish I had that resource when doing 281. Google "Visualizations of Algorithms and Data Structures", and the correct site has a color scheme containing green and animation so many algorithms and data structures. I sent you the link before.

#### So what does this have to do with recursion?
  
Well, for one, they are how the computer runs recursive functions. In memory, there is a region designated as the program stack, filled with stack frames. A stack frame is a section of memory which holds the state of the program when a function call is made. All local variables, argument variables, and return values all get pushed on and popped off of the stack. 

Here we have our dilemma; every recursive call to a function results in the allocation of a new stack frame. This takes time and memory. Every call results in the allocation of new local variables and arguments, which takes a lot of memory. In addition, there is only one program stack per thread, and they tend to be fairly limited in size. If you push too much onto the stack, it will overflow.   
So what can you do to keep the behavior of a recursive function without the performance and memory penalties? Allocate a stack on the program heap of course(when you do calls to `new()` and `malloc()` you allocate memory on the heap.) If you save the appropriate data on your heap-based stack, the algorithms will perform identically, and your new version will be much faster.

#### Solving recurrence relations
I won't speak about recurrence relations, including solving them with telescoping or the Master theorem here, as odds are you won't be asked to solve a recurrence relation. It's good to have this math background though in case they do though. 

As a side note, I'd recommend learning how to solve the Fibonacci sequence in O(log n) time though with the closed form solution, which I have heard come up in interviews multiple times.

### Linked lists
These aren't so common in Python, but in C++ they're used a lot. All you have to know is that these are used to implement variable length arrays. A linked list is composed of a series of nodes, where each node contains a value, as well as a pointer to the next element(and sometimes to the previous element). To add a new element, you allocate a new node on the heap, set the list's last node's next pointer to point to the new element, and the new node's previous pointer to point to the former last element. The nice thing about Python is you don't have to worry about this :)   
(As a side note, C++ has this functionality in std::list. Vectors are always stored contiguously in memory, and if space runs out, it is reallocated, expanded, and copied to the new location.)

### Standard Libraries
Learn the standard library of the language of your choice. This will help you by allowing you to avoid the process of implementing data structures and common algorithms by yourself, instead providing you with high quality implementations.

### Queues
A queue is very similar to a stack, in that it also supports the operations `put()`(I called it `push()` before, but it's called `put()` in Python) and `get()`(a.k.a. `pop()`), but instead of the most recent items getting popped, it's the first items which were pushed on that get popped out(first in, first out, or FIFO.) Python has these in its standard library in the Queue module. To declare one, do

```
import Queue
myQueue = Queue.Queue()
myQueue.put(5)
myQueue.put(10)
front = myQueue.get()
print(front) #is 5
```

You can also implement a stack-like LIFO data structure using Queues too, using `Queue.LifoQueue()` in Python.

#### Priority Queues
A priority queue is a queue with a special property: each element is assigned a priority. In max-priority queues, the element with the highest priority is returned first. In min-priority queues, the element with the lowest priority is returned first. By default, the `Queue.PriorityQueue()` in Python is a minimum priority queue. In Python, you can push anything that can be sorted on a priority queue. A common pattern is to push a tuple like `(priority, value)` (remember, tuples are immutable, so if you need to change the priority, you need to completely replace it with a new object). Python sorts refer to the first object in a tuple, then if there is a tie, the second, etc (this is the way strings are compared as well.)

For more information on the Queue class, see the Python documentation.

So what about the complexity? If we sorted upon every insert and removal, we'd have a worst case time complexity of both of those operations of O(n log n). However, it turns out with the Heap container, we can get that down to O(log n). I'll talk about this later.

#### Deques
This is a funny one. It's a data structure that supports both pushing and popping from both ends. 

### Container Types
There are ordered and unordered containers. The main difference is that you can use binary search for O(log n) finds on sorted containers (as opposed to O(n) on  ordered containers.) Consequently, addition and removal are slower on sorted containers compared to ordered containers( you can't simply append on sorted containers.)

### Sets
Sets in Python are collections of unique, hashable objects(if you don't know what a hash is, I'll explain it right now. 

### Hash tables
Hash tables are arguably the most important data structure known to man. Unlike sorted containers which allow O(log n) lookup, these allow O(1) lookup. How do these data structures which are the programming equivalents of unicorns work?

The underlying data structure of a hash table is an array in memory. You have two other components: the hashing function, and the collision resolution scheme. 

#### Hash functions
All a hash function does is turn a value into an array index. The hash function in turn is composed of two parts.

The first part, the *hash code*, takes a value and returns an integer. A function that always returned zero would be a hash coding function, but it would be a terrible one. More terrible ones include adding the ASCII values of a string together, multiplying the digits of a number, etc. A good hashing function minimizes the chance of a hash collision; a hash collision is when two distinct values have the same hash code. Good hashing functions, like SHA-256, have extremely small probabilities of hash collisions. I've heard that it's much more likely that a giant asteroid will impact the earth than a collision of SHA-256 ever happening in the wild. 
The second part of hash functions is the *compression mapping*. All this does is maps the integer to an array index using the modulus operator and the length of the underlying array.

A good hash function should be extremely fast to compute. Cryptographic-strength has functions often are relatively slow to compute, so faster ones are used that have higher collision rates. So how do we manage collisions?

### Hash Collision Resolution
There are four methods of hash collision resolution I will talk about. These are

* Linear probing
* Quadratic probing
* Separate chaining
* Double hashing

#### Linear Probing
If a hash collision occurs(that is, if the value at the index returned from the hash function is different than the hashed value), the probe goes to the next element in the array. If an empty position in the array is found, the element is inserted there. Searching operates much the same way.

To remove an element, the most efficient way is to mark it as "deleted", and maintain the positions of all of the other elements in the array. Otherwise, you'd have to rehash all of the elements in the array to avoid erroneous misses.

#### Quadratic Probing
Quadratic probing is like linear probing, but instead of the probe moving linearly, it moves quadratically increasing distances away from the collision. This provides a more even spread of elements across the hash table (linear probing tends to have a lot of clustered elements, which decreases the efficiency of the hash table.

#### Double hashing
If a hash collision occurs, the hash function is reapplied to the hashed value. This is not a recommended method, as during lookup, each element must be hashed up to twice. In addition, if your hashing function returns 0 every time, you might get an infinite loop. Sucks.

#### Separate Chaining
This is a very common method of collision resolution. Instead of values being placed directly in the underlying array, each array index holds another array. Each insertion to the table just expands the subarray. During lookup, the subarray is linearly searched, resulting in a worst case time complexity of O(n) lookup. In practice, it's much better. 

A great hash table will have a low load factor. What is load factor? Load factor, represented by a lowercase alpha, is equal to N/M, where N is the number of keys placed in an M sized table. For separate chaining, this is equal to the average number of elements in each subarray. For probing, it's the percentage of table positions occupied. That's pretty much all you need to know about hash tables!


### Sets, continued
Back to sets! So in Python, sets are hash tables. To iterate over them, the computer just takes your underlying array, and iterates over the elements which are set. To see if an element is present, it just looks up the hash of the element and see if the corresponding array position contains an element. Note, in C++ STL, these are implemented with sorted containers, and have O(log n) lookup time.

As a side note, Python's dict class is also implemented with hash tables.


### Sorting
I'm too lazy to write this section, as I learned sorting by looking up GIFs on Wikipedia. To learn it I suggest that you use the 281 lecture #10 and that really awesome data structure and algorithm visualization website. It won't take you long, I promise. But first, read the rest of this section, as well as the heap section, as it will help with heap sort.

There are some other things worth briefly saying about sorting. They all have distinct advantages; know when it's best to use sorts (for instance, insertion sort is really good to use when you need to put a new element into a list, bubble sort is greater for lists that are almost totally sorted, etc). Also, the theoretical limit for comparison based sorts is O(n log n), but bucket sort and radix sort can do better than O(n log n), which is pretty cool.

Learn these really well, as many many interview questions depend on them. Know how to implement AT LEAST binary, insertion, quick, merge, heap, and binary, and bucket sort and radix sort will impress people. For details about heaps and heap sort, look below as well.

### Heaps
What if you wanted a data structure that allows you to easily and quickly pop the most extreme element? Heaps allow you to do just this.

They often use binary trees as their underlying data structure.

### Trees
Trees are really important data structures. Go look at 281 lecture 11.
Binary search trees are also important to learn, look at 281 lecture 16.

AVL trees are basically balanced binary trees. These aren't important to learn for interviews, but they're fairly easy to understand so you might as well. Let me teach these to you in person.

### Heaps in Python
Priority Queues. Nuff' said.

### Graphs
These are really hard to explain well without pictures. To learn them, look at the 281 slides from 20 and up in conjunction with the data structures and algorithms visualization site. I think you already have a pretty good background due to 203.

### The rest of 281 material(only like 4 lectures or so)
This is the advanced stuff that puts all of the other stuff together. Read over this, don't spend time on anything if you don't understand it, and ask me about it when I get back.

If you've made it through this guide and aren't totally confused, pat yourself on the back! You've compressed most of the material taught over 3.5 months into a small document! You probably don't understand all of the material, but that's alright, that's what Google is for.

### How do you effectively use the knowledge above to do interview questions? 
When you get an interview question, first make sure you've fully understood the problem. Getting the correct idea of what the interviewer is asking is most of the battle once you know algorithms and data structures, so ask for clarification throughout the process about the question itself, limitations, edge cases, etc. 

Once you have a basic idea of what the question is, then choose the right algorithms and data structures for the task. Make sure to tell the interviewer why you chose them(read: tell them the big O complexities, this will impress them.) Then, it's just a matter of putting it together with code.

### Style
Write very small functions which are easy to understand (unless time is REALLY an issue, in which case, do whatever is fastest). Premature optimization is the root of all evil. Those basically are the only two things you have to worry about in these questions. 
### Where do you go from here?

Practice. Practice more. Practice more than that. The more you get used to the process, the easier that it becomes.

Learn fancy data structures and algorithms. Learn Bloom filters (these allow constant time set intersections, which is pretty badass, among other things). The wider your knowledge about crazy data structures and algorithms, the more you'll potentially impress the interviewer. The best is mentioning a great data structure the interviewer has never heard of. This basically guarantees you'll do well.

Expand your knowledge of Python and other languages. The more fluent you become, the easier the interview becomes, until it becomes basically effortless.

Learn optimization techniques. This requires a knowledge of the EECS 370 stuff, as when you know how the processor works, you can often tune your programs to take advantage of the architecture. Mostly, this is just exploiting spatial locality, memory organization(the order of variables in a struct matters), and knowing what operations take a lot of cycles. Don't worry about this too much for now.

Most importantly, do side projects. With good side projects, you can nail the behavioral questions, and often bypass the technical interview (and everything else about the interview process for that matter.)   
Finally, relax. If you know the material, do the stuff recommended in the guide, and put in a bit of interview practice, you'll ace most of them. If you totally bomb a part of the interview, don't let it affect you, most other people probably did too, and you'll still probably get the job(you won't if you make a big deal out of your mistakes.)

Michael
12/22/2013




 


