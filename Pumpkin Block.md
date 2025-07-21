Each pumpkin block is implemented in `pumpkin/src/block/blocks`

Here is an example of registering a block:
```rust
#[pumpkin_block("minecraft:barrel")]
pub struct BarrelBlock;
```

The macro that the block implements `pumpkin_block` is a custom macro that automatically defines the metadata (namespace and id) of the block(s) that this implementation will cover. A more advanced solution looks like:
```rust
pub struct MushroomPlantBlock;

impl BlockMetadata for MushroomPlantBlock {
    fn namespace(&self) -> &'static str {
        "minecraft"
    }

    fn ids(&self) -> &'static [&'static str] {
        &["brown_mushroom", "red_mushroom"]
    }
}
```

As you can see here, we needed to manually implement the metadata for these blocks.
After the metadata is added for the block, you can add it to the registry. This is done in `pumpkin/src/block/mod.rs`, and registers it for performing implemented actions when the player/server needs them. These actions that get called are implemented in the `PumpkinBlock` impl for each struct:
```rust
#[async_trait]
impl PumpkinBlock for TNTBlock {
	// impl for the block
}
```

Here you have the ability to implement functions like `placed`, `on_neighbor_update`, `random_tick`, `get_weak_redstone_power`, and many more.

Note: The code in pumpkin should always match [[Vanilla]]