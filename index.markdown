---
title: Reinventing the wheel
layout: default
---

> If you can't understand compilers, then you can't understand computer science.
Eric S. Raymond

# Reinventing The Wheel

## Introduction

This project is about understanding some fundamental questions about
computation and, ultimately, abstraction.

The purpose here is to create a full stack of abstraction, from the lowest
possible level of Turing-Complete computation up to a high level programming
language.  This can be achieved, of course, by means of a stack of compilers.

The choice of the lowest ground is a esoteric computer language kindly called
"Brainfuck". We have considered using, the literature canonical, Turing Machine
itself, but it happens that the latter is even more complex than the former in
what touches the implementation of a interpreter.

In other words, what we mean is, the Brainfuck interpreter is much more simpler
than a Turing Machine interpreter.

## The Brainfuck

A Brainfuck program has an implicit byte pointer, called "the pointer", which
is free to move around within an array of 30000 bytes, initially all set to
zero. The pointer itself is initialized to point to the beginning of this
array.

The Brainfuck programming language consists of eight commands, each of which is
represented as a single character.

* `>`   Increment the pointer.
* `<`   Decrement the pointer.
* `+`   Increment the byte at the pointer.
* `-`   Decrement the byte at the pointer.
* `.`   Output the byte at the pointer.
* `,`   Input a byte and store it in the byte at the pointer.
* `[`   Jump forward past the matching ] if the byte at the pointer is zero.
* `]`   Jump backward to the matching [ unless the byte at the pointer is zero.

The semantics of the Brainfuck commands can also be succinctly expressed in
terms of C, as follows (assuming that `p` has been previously defined as a
`char*`):

* `>`   becomes     `++p;`
* `<`   becomes     `--p;`
* `+`   becomes     `++*p;`
* `-`   becomes     `--*p;`
* `.`   becomes     `putchar(*p);`
* `,`   becomes     `*p = getchar();`
* `[`   becomes     `while (*p) {`
* `]`   becomes     `}`

## The abstraction stack

What a compiler or interpreter really does is sealing of on level of
abstraction into the other. It's important to note that, every computer
language, no matter how high-level it its, ultimately, must be translated into
the same boring machine code, in order to be understood by the processor. It
(the processor) doesn't understand high-level programming of any kind, just the
plain old assembly.

In this program, the Brainfuck is our bottom level, the "assembly" so to call.
Note though, that a assembly-like language itself will emerge from the first
level of abstraction, hence, in a way, our Brainfuck is even lower in the
abstraction chain than the known assembly itself!

Now, let's for a moment reflect on what we mean by climbing up the abstraction
mountain. Starting with an analogy: one can describe a gas within a recipient
by its temperature, pressure and volume, likewise, one can describe the same
system by enumerating all particles along with their positions and velocities.

It's obvious that the temperature-pressure-volume (TPV) description is on a
higher level. Indeed, those attributes are nevertheless an emergence from the
lower level buzzy collisions of a myriad of atomic-level molecules.

Although both descriptions are valid, we rather describe the system in the TPV
form, as we do, by analogy, like to program in a higher level of abstraction
than to write thousands of assembly instructions.

What the compiler does for us, is to translated form the TPV description into
particle description, and, forcing or analogy a bit, even this particles
description can, in principle, be an emergent behavior from an even lower level
reality (e.g. the zeros and ones in a computer circuitry).

In a sense, higher level emergence can not be fully understood by looking only
at a lower level machinery, for instance, it's very hard to explain a car by
speaking about all of its atoms and their interrelations. Yet, one can find it
useful to go up in the abstraction and talk about motor, wheels, gas, etc.

I the same way, after a language is compiled, it does not concern us (at least
in functional matters) to read the compiled code, there must not be necessarily
a one-to-one isomorphism between higher level constructs and blocks of lower
level code, as there isn't in a gas a special particle for temperature, other
for pressure and another for volume. They all together play roles that happens
to emerge in a higher level the TPV observance.

As happens to be, computer programs can be reductionist only at the same
abstraction level, for when a compiler does its job, one can only truly
understand the workings when given a holist perspective.

## The Goal

Our goal here is to produce a useful, open-source manifesto of working-code and
clear text on how exactly does compiler escalates abstraction from one language
to the next. A secondary, but important goal, is also to learn a lot along the
way.


## Projects

### [Brainfuck](http://github.com/reinventingthewheel/brainfuck)

An optimized brainfuck intepreter that will be used to run our brainfuck
programs.


### [Micro Assembler](http://github.com/reinventingthewheel/micro-assembler)

An assembler built for assembling programs from a very limited assembly language
(almost machine code) to brainfuck "bytecode".


### [Assembler](http://github.com/reinventingthewheel/assembler)

This is the second step in abtraction from the brainfuck machine.
It's a assembly to micro-assembly compiler.

