---
title: React Hooks
description: 
published: true
date: 2022-11-30T02:11:39.862Z
tags: react
editor: markdown
---

# Downsides / Pitfalls
- Hooks are call-order sensitive and cannot be conditional.
- Variables declared in a React component can be captured by a hook closure and become "stale" if the developer fails to pass in the correct dependencies array. This leads to React developers relying on ESLint rules to ensure correct dependencies are passed. However, the rule is often not smart enough and over-compensates for correctness, which leads to unnecessary invalidation and headaches when edge cases are encountered.
- Expensive computations require the use of useMemo, which again requires manually passing in the correct dependencies array.
- Event handlers passed to child components cause unnecessary child updates by default, and require explicit useCallback as an optimization. This is almost always needed, and again requires a correct dependencies array. Neglecting this leads to over-rendering apps by default and can cause performance issues without realizing it.
- The stale closure problem, combined with Concurrent features, makes it difficult to reason about when a piece of hooks code is run, and makes working with mutable state that should persist across renders (via useRef) cumbersome.
- 