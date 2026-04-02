# Growtopia Auto Plant + Take Seed

This repository contains a Lua script designed to automate the process of planting seeds and retrieving them from a storage world in Growtopia. The script is intended to be used with the **Pandora** execution software.

## Script Overview

- **File**: `Auto Plant + Take Seed.lua`
- **Authors**: @Vency, @Edison, @Arl3y
- **Date**: 9/16/2022
- **Purpose**: Automates planting of a specific seed type across a target world and automatically warps to a save world to pick up more seeds when the inventory runs out.

## Configuration Setup

Before running the script, you must configure the variables at the top of the file to match your account and world setup. Open the script and modify these values:

### World & Save Info

```lua
World_Name = "Contoh" -- The name of the world where you want to plant the seeds.
World_Save = "Contoh" -- The name of the world where your seeds are stored on the ground.
Door_ID = "Contoh"    -- The required Door ID to warp into your worlds.
```

### Seed Info

```lua
Seed_ID = 4585 -- The Item ID of the seed you want to plant. 
```

### Delay Settings

```lua
Delay_Plant = 400      -- Delay for planting actions. Preferred range: 200-400 ms.
Delay_Warp = 5000      -- Delay when warping. Maximum of 7000 ms to avoid getting banned.
Delay_Find_Path = 1000 -- Delay for finding paths. Preferred value: 1000 ms.
```

## How It Works

1. **Initialization**: The script starts by warping to `World_Name` via the `Main()` function.
2. **Planting (`plant` function)**: It iterations through world coordinates searching for appropriate, open tiles with solid blocks underneath and begins planting the designated `Seed_ID` using the defined `Delay_Plant` interval.
3. **Restocking (`takeSeed` function)**:
   - The script continuously monitors your inventory amount.
   - If the seed count reaches `0`, it triggers the restocking phase.
   - It warps to `World_Save` using the `Door_ID`.
   - It searches the world objects for floating seeds matching `Seed_ID`, finds the path to them, and collects them.
   - Once picked up, it naturally resumes the planting flow back in `World_Name`.

## Disclaimer

Note that botting scripts violate Growtopia's Terms of Service and might result in a ban. Use at your own risk.