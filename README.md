# GAL-LINE: How to Make a Very Serious Game With JavaScript

### A book about making a commercial web game, written while making the game.

[Read the book →](gal-line-book.github.io)  
[Source code →](github.com/homogaragensis/gal-line)  
<!-- Play GAL-LINE → -->

## Development status
This is **not a finished textbook**. Some chapters don't exist yet, some things will change, and some code will inevitably be rewritten.

Future chapters may even contain evidence that we had absolutely no idea what we were doing.

## What is GAL-LINE?

**GAL-LINE** is a silly and vaguely satirical arcade game about chickens, legs, and train stations.

It's deliberately simple: a chicken runs forward, encounters a leg beyond the yellow line, and you hit it. ***Very quickly***. Eventually, the leg gives up and moves away.

There are power-ups, strange characters, increasingly unreasonable situations, and probably several terrible design decisions.

The simplicity of the game, and the fact that it runs in a browser, makes it a useful excuse to explore how a complete game can be built with **HTML, CSS, and vanilla JavaScript**.

This repository contains the source of the accompanying development book. Rather than building the game first and turning it into a tutorial afterwards, 
the book is written **alongside the development of the game**.
Each chapter documents a stage of the actual process, using the code being written at that point.

In other words: the tutorial and the game are being made together.

## The Relation With the Source Code

Since each chapter corresponds to a stage in the development of **GAL-LINE**, 
at the end of each of the book's chapters there will be a link to the corresponding commit in the game's Git history.

This will let the user explore the codebase times at which each progress was made.

The project therefore has two complementary parts:

- **The book** explains the decisions, ideas, and implementation.
- **The game repository** preserves the actual code and development history.

You can follow the project chronologically, jump between chapters and commits, or simply steal whatever bits of JavaScript you find useful.

## Why Vanilla JavaScript?

Because we wanted to see how far we could get without hiding the game behind an engine.

*GAL-LINE* uses ordinary web technologies:

- No game engine.
- No JavaScript framework.
- No grand plan.

> This is also part of what the humble *Homo Garagensis* is trying to preach: technological simplicity in an age of increasingly convoluted infrastructures.

## License

The **book and its original written content** are licensed under [Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)].

The **source code presented in the book** is licensed separately under the MIT License.

GAL-LINE's **artwork, characters, audio, logos, and other proprietary creative assets** are not covered by these licenses.

See `LICENSE` for the book license and the game repository for the code license.
