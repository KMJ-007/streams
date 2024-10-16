---
title: MersenneTwister19937
date: 2024-08-11
tags:
  - seed
enableToc: false
---
```js
import { MersenneTwister19937, integer } from "random-js";

/**
 * Hashes a string to a 32-bit integer.
 * @param {string} seed - The input string to hash.
 */
function hashString(seed: string) {
	let hash = 0;
	for (let i = 0; i < seed.length; i++) {
		const char = seed.charCodeAt(i);
		hash = (hash << 5) - hash + char;
		hash |= 0; // Convert to 32bit integer
	}
	return hash;
}

/**
 * returns a function that generates same sequence of random numbers for a given seed between 0 and 1.
 */
export function seededRandom(seed: string) {
	const seedHash = hashString(seed);
	const engine = MersenneTwister19937.seed(seedHash);
	return () =>
		integer(0, Number.MAX_SAFE_INTEGER)(engine) / Number.MAX_SAFE_INTEGER;
}

```

this is really cool algo, i need to deep dive into this and explore this rabbit hole



https://arxiv.org/pdf/2309.16682