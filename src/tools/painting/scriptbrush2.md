# Script Brush

The Script Brush is a very powerful tool, it processes Lua code input which can be used to alter blocks based on multiple conditions.

Assuming you know some programming basics, this documentation will teach and simplify the tool in it's entirety. 

The Lua programming language is similar to Python, but is more lightweight. Hence why it was used in the mod.

### Script Examples

Even though the Script Brush can do almost anything, there are some things that it can't do so well. These include generating structures or anything that requires hard coding. The following examples may vary in difficulty.

- Terrain Generator
- Texturing Brush
- Rock Generator
- Crop Painter
- Spike Generator
- Cave Generator

## Tool Options

The [Tool Options](/editor/windows/tooloptions.md) window is used to enter code. [Presets](/editor/toolpresets.md) can be used to save code to be used later.

## Custom Variables

These two variables allow you to interact with coordinates and retrieve Blockstate IDs.

### x, y, z

The values of these three variables represent the position of the [Target Block](/tools/intro.md#target-blocks). Meaning using these three values is much better than hardcoding specific coordinates.

```lua
if y<=100 then
    -- Do Something
end
```

### blocks

The blocks object (or table) allows searching for Blockstate IDs. Blockstate IDs are numerical values used to represent a block state. You shouldn't use these values directly as it can get confusing. 

> Blockstate IDs are not the same as Block IDs[^note1].

```lua
dirt=blocks.coarse_dirt
```

## Custom Functions

Custom functions allow for further use of the two variables when combined.

### getBlock(x,y,z)

Returns the Blockstate ID value for the given coordinate. This function **does not** return a Blockstate ID with block properties.

In this example, I use `return` to place a block at the [Target Block](/tools/intro.md#target-blocks) position using `blocks.dirt`. Not to be confused with setBlock.

```lua
if getBlock(x,y,z)==blocks.grass_block then
    -- get the target Blockstate ID and check if it matches the grass_block Blockstate ID
    return blocks.dirt
end
```

### setBlock(x,y,z,`Blockstate ID`)

The setBlock function is another method to place blocks. Unlike using return, the position can be added without stopping the script.

An offset to the block placement can be added as it uses the XYZ variables. Using the setBlock function instead of return enables the ability to set more than one block for every Target Block process.

```lua
carpetFitForAKing=blocks.pink_carpet

if getBlock(x,y-1,z)~=blocks.air and getBlock(x,y,z)==blocks.air then
    -- only allows blocks with an empty block above
    setBlock(x,y,z,carpetFitForAKing)
    -- changes the block at the target block position
end
```

### isSolid(`Blockstate ID`)

The isSolid function returns a boolean if the block has a solid collision box.

```lua
--Represents solid blocks with lime wool, everything else is represented with red glass

currentBlock=getBlock(x,y,z)

if isSolid(currentBlock) then
    setBlock(x,y,z,blocks.lime_wool)
else
    setBlock(x,y,z,blocks.red_stained_glass)
end
```

### getHighestBlockYAt(x,z)

Returns the Y axis value for the highest block at the given x and z position. Unlike the other functions, this one returns a number between -64 and 319.

```lua
highestBlock=getHighestBlockYAt(x,z)

if highestBlock > 100 then
-- checks if the highest block is above Y=100
    setBlock(x,highestBlock,z,blocks.snow_block)
end
```

### withBlockProperty(`Blockstate ID`,`Property=Value`)

The withBlockProperty function allows for adding properties to existing Blockstate IDs. This removes the limitation of using the [blocks object](#blocks) to set blocks in the world.

```lua
--Replaces wheat with its fully aged variant

if getBlock(x,y,z)==blocks.wheat then
    agedWheat=withBlockProperty(blocks.wheat,'age=7')

    setBlock(x,y,z,agedWheat)
end
```

### getBlockState(x,y,z)

Unlike [getBlock](#getblockxyz), this function returns the exact Blockstate ID for the provided coordinate. 

```lua
--Replaces fully grown wheat with new wheat

currentBlockState=getBlockState(x,y,z)
--gets the exact blockstate ID for the target block 

agedWheat=withBlockProperty(blocks.wheat,'age=7')
newWheat=withBlockProperty(blocks.wheat,'age=0')
--defines fully aged wheat and new wheat

if currentBlockState==agedWheat then
--check if the target block is wheat with the age of 7
    setBlock(x,y,z,newWheat)
end
```

### getBlockProperty(`Blockstate ID`,`Property`)

The getBlockProperty function returns the value for the provided Blockstate ID and Property. Block Properties[^note2] are attributes used by Minecraft to determine things like stair rotation and redstone power levels.

```lua
--Checks if the target block can be waterlogged, and waterlogs it if possible

currentBlockState=getBlockState(x,y,z)

if getBlockProperty(currentBlock,'waterlogged')=='false' then
    --Checks if the block isn't waterlogged. Only waterloggable blocks have this property

    waterloggedBlock=withBlockProperty(currentBlock,'waterlogged=true')
    --Gets the waterlogged variant of the current block
    setBlock(x,y,z,waterloggedBlock)
end
```

## Notes

[^note1]: [Block IDs](https://minecraft.wiki/w/Java_Edition_data_values/Pre-flattening) were swapped out in favour of the new Blockstate IDs in [1.13](https://minecraft.wiki/w/Java_Edition_1.13).

[^note2]: [The Block Properties Wiki](https://minecraft.wiki/w/Block_properties)
