Random ticks are a type of tick in minecraft that allow for stuff like:
- Crop growth
- Mushroom spread
- Leaf decay
- Farmland hydration
- Grass spreading
- Lava lighting

# Calculations
For each game tick (default 20 tps (ticks per second)), each [subchunk](Chunks#SubChunk) gets by default 3 random tick positions.

Every block then has `(3/(16*16*16))`, or 0.073% chance of being ticked in a given tick.
That means that at 20 tps, `100/(20 * 0.073%)`, each block is expected to random tick once in about every 68 seconds.

For 50% of blocks in a chunk to be random ticked it is expected to take approximately: $$\log_{\frac{4096-3}{4096}}(0.5) \approx 946.03\ ticks$$
, or 47.30 seconds.