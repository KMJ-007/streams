---
title: rust
date: 2024-05-20
tags:
  - seed
enableToc: false
---
not able to understand, need to revisit this blog again in the future:

https://graydon2.dreamwidth.org/312681.html

**# Chapter 3

### Partho

- constant evaluation
    
- scoped shadow
    
- integer literal
    
- integer overflow
    
- char is weird
    
- array is limited
    
- array indexing diff from tuple
    
- rust is an expression-based language
    
- we could replace match with if in the guessing game
    
- rust if else and loops are pretty similar to python in syntax
    
- loop labels are neat
    
- in last for range example upper bound is not included
    

- (1..4) not included
    
- (1..=4) included
    

### Karan

- How mutability affects performance and memory?
    
- If we have concept of shadowing then what's the point of mutability, scoped shadowing is useful though
    
- We can't change the type of the variable if we use mut, and that's why shadow comes in handy
    
- Int overflow in release can cause some weird bugs, because it wraps them to the starting position 
    
- If and else both return type also should be same is like weird, compare to other language, rust want to be very sure about all the possible outcomes of program at compile time, taki runtime par kam se kam bugs aaye aur reliability de sake wo
    

# Chapter 4.1

### Partho

- rust compiler is really nice!
    
- still kinda confused with stack and heap like i get the data structure but don’t know how it fits into the big picture (probably later in the chapter they explain)
    

- stack = fixed (tuple, array)- memory allocated at compile time
    
- heap = variable (vector, string)- memory allocated at run time
    

- we have hardcoded string with like “” (immutable, stack) and then we have String type (mutable, heap)
    

- ok so sidenote rust doesn’t really give you an error if you add ‘mut’ to immutable stuff like tuple and “”
    

- apparently tuple and stuff can be mutable
    

- stack is copied and heap is moved (one owner)
    

- compared to python where well you could run into bugs cuz data is shared because of shallow copy
    
- no concept of shallow copy
    

- Copy trait hmmm
    

### Karan

- "None of the features of ownership will slow down your program while it’s running." But it slows the development, but it also depends on timeline which you are viewing it, longer term vs short term
    

- this is kindof meta thing for rust compared to other languages
    

- Each value in Rust has an owner.
    
- There can only be one owner at a time.
    
- When the owner goes out of scope, the value will be dropped.
    
- Stack feels little restrictive,use when you are sure you know the limits, heap gives more freedom, like string or if we want to create dynamic size array like other languages 
    
- The heap and stack thing is interesting, but the example s1=s2, the s1 is no longer considered valid, i understand the double free memory error, but it feels like wrong somehow
    
- Koi bhi chij jo heap ka use karke copy karne ka try karo ge wo copy karne ki jagha sirf pointr bana dega, like error says it don't have copy trait, string copy wale example mai
    
- Ownership for heap = move
    
- Ownership for stack = copy
    

# Chapter 4.2 and 4.3

### Partho

- dereferencing
    
- can’t do any more reference if there is a mut reference in scope
    

- scope here is kinda diff
    

- no dangling references (another rust memory safety feature)
    
- using & in pattern
    
- slices are reference
    
- String / string literal / string slice 
    

### Karan

- Multiple mut reference can’t exist at the same time in same scope, is little strange for me
    
- And immutable and mutable can’t exist at the same time
    

- At any given time, you can have either one mutable reference or any number of immutable references.
    

- No dangling  references (lifetimes is smt to consider)
    
- I got the theory but will more understand this whole saga of slicing, ownership when i write more code!
    

# Chapter 5

### Partho

-   
    

### Karan

- Struct feels like classes and objects and their method
    
- Why spread operator in rust is two dots and not 3, like there are too many things one need to unlearn to learn rust if you are coming from ano lang 
    
- Struct can store both structure data and unstructure data(tuple struct)
    
- Lifetime is new kid in the house, aage dekhte hai jab aata hai tab
    
- Is this name convention ki structure hamesa capital letter se start hoga?
    
- Println don’t take ownership but it takes ownership
    
- Didn’t fully understood the automatic referencing
    
- Impl and methos now makes sense, still dind’t get the Self sometime they are using self and sometime Self, even compiler was giving me error
    

  

# Chapter 6

### Partho

-   
    

### Karan

- Option enum is very useful, now we have more breathing space
    
- There is no switch case in rust so we have match pattern matching, but it is just more restrictive you need to handle the all the default cases like none if we use options enum
    
- If let is useful thing, when handling only one conditional statement and don’t want to write whole pattern matching
    

  

# Chapter 7

### Partho

-   
    

### Karan

- Two types of crates, binary crate(main.rs)(must have main function) and lib crate(lib.rs)(don’t have main function)
    
- Crate meaning in rust is basically a lib
    
- Cargo.toml is like package.json
    
- I think i so far understood what it is trying to say, but wordings are little confusing for first time, will get it more when do things, the confusing part is at most only one library crate can be there in package  
    “A package can contain as many binary crates as you like, but at most only one library crate. A package must contain at least one crate, whether that’s a library or binary crate.”
    
- You can create individual modules for separating the code logic, and import the code from other file, i liked how there is no default export, like we have in python and js, and because of that there is no need to use __main__ and export default thing, which is sometime confusing, jo chayie utna mangwalo use karo baat khatham
    
- Ye thoda samjh mai aaya modules wala, kese submodules mai code ko divide kar sakte hai, jese jese work karenge ese jyada samjh aayega
    
- Same thing as other languages have absolute path and relative path
    
- Super keyword is used for going to parent module and starting the path from there
    
- Struct mai sabhi fields ke aage pub likhna padega whereas enum mai sirf ek pub se sari field public ho jayegi
    
- Reexporting seems interesting feature, will get more idea when use in the application
    
- Learned about how to break down code into multiple files using mod and use keywords
    

  

# Chapter 8

### Partho

-   
    

### Karan

- New collections are vector, string and hash map
    
- Vectors are basically dynamic array
    
- Get method is more safer compare to direct indexing, because out of range wale mai program crash nahi hoga aur None return kar dega
    
- Ownership and borrow checker will take some time to get used to the concept
    
- Vectores can only store the values that are the same type, but to overcome this we can use enum
    
- Under the hood string is just vector of u8(ascii value)
    
- Indexing of string is not possible in rust, because the way it stores the value of the string, and it is not sure to return what byte, character, or grapheme cluster, just use slicing 
    
- I think rust has made string little complicated compare to other lang, it is because of they are giving utf-8 by default([https://news.ycombinator.com/item?id=26811879](https://news.ycombinator.com/item?id=26811879))
    
- In hashmap types of all the keys should be same and types of all the value should be same
    

  

# Chapter 9

### Partho

-   
    

### Karan

- Panic is interesting, recoravable and urecovrable errors are not lot of programming languages provide form what i have seen
    
- Backtrace kab karna pade wo pata nahi exactly, use karenge jese jese rust wese pata chalega i guess
    
- Finally unwrap is here in the chapter, bahaut jagha par dekha ye mene logo ke code mai
    
- Error propagation is really useful compare to it’s alternative
    
- Question: is it advisable to use unwrap and expect in production(release) code ?
    
-   
    
- ![](https://lh7-us.googleusercontent.com/docsz/AD_4nXcLK0xL-5ROaWf5peAnKos2TrvU2mOAmtr4C0uwrtLKOSy0wldaYZ_M1U-Scu2gGYhNgsJ30G_-1RqPDg-xIGnwxmZKwY7u9ap3fgedgBMi7Y-GrUDNHvnFDl0ByAhh8ng_kAz9A7Vg99hVz_DbqXeqdPc?key=ba2YTbStVGCAbOz9RYT2SA)
    
-   panic is for unrecoverable errors, whenever we need to stop the execution of the program we use panic
    

# Chapter 10:
i already knew generic programming so it was not something new in rust also, i have cried enough in typescript to get this current feeling,

one thing i liked about rust is there is no runtime cost or overhead when you use generics in rust, cuz we have our lovely compiler which comes here to help us

>You might be wondering whether there is a runtime cost when using generic type parameters. The good news is that using generic types won't make your program run any slower than it would with concrete types.

>Rust accomplishes this by performing monomorphization of the code using generics at compile time. _Monomorphization_ is the process of turning generic code into specific code by filling in the concrete types that are used when compiled. In this process, the compiler does the opposite of the steps we used to create the generic function in Listing 10-5: the compiler looks at all the places where generic code is called and generates code for the concrete types the generic code is called with.

ex.

```rust
// written code:
let integer = Some(5);
let float = Some(5.0);


//compilor will turn this into
enum Option_i32 {
    Some(i32),
    None,
}

enum Option_f64 {
    Some(f64),
    None,
}

fn main() {
    let integer = Option_i32::Some(5);
    let float = Option_f64::Some(5.0);
}
```

i tried very hard, watched lots of videos, but i didn't understand the lifetimes in rust, maybe more i will use it, i will get more idea and intuition about this, but this thing is really confusing 

# Chapter 11:
testing is important, i learned few things while writing lisp intrepreter in rust

if i run the test, and there are multiple test then it will run in parallel, lot of things i read in the chapter, but i think as i will write more test i will get more gist of it, and i should keep habit of writing test from the beginning 

# Chapter 12:
it's project time yes!!!!
