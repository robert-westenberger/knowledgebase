---
title: Typescript
description: 
published: true
date: 2022-08-18T15:20:31.023Z
tags: typescript
editor: markdown
---

# Types vs Interfaces
## Use Interfaces Over Type Aliases
You will get better error messages.
## Interfaces are Open, Type Aliases are Closed
This means you can extend an interface by declaring it a second time.

```
interface Kitten {
  purrs: boolean;
}

interface Kitten {
  colour: string;
}

const pretty_kitty: Kitten = {
  purrs: true,
  colour: 'red'
}
```

A type cannot be changed outside of it's declaration.

```
type Puppy = { // this errors
  color: string;
};

type Puppy = { // this errors
  toys: number;
};
```