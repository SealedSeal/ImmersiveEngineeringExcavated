![Logo](https://raw.githubusercontent.com/BluSunrize/ImmersiveEngineering/master/src/main/resources/assets/immersiveengineering/logo.png)
--------------------------------------------------

A retro-futuristic tech mod!
Wires, transformers, capacitors!
--------------------------------------------------

4ClevDev edit of original mod with some changes, especially reworking excavators.
--------------------------------------------------

Changes:

  * Excavator:<br/>
    * Mineral Vein:<br/>
      + Reworked code structure of minerals<br/>
      + Minerals are now not hardcoded and moved to json file inside confing folder IEMinerals<br/>
      + Added handler for json confings of minerals<br/>
      + Added support for non ore dictionary names (minecraft:iron_ore)<br/>
      + Added support for names with metadata (minecraft:stone/1)<br/>
      - Removed vein size from general config<br/>
      - Removed blacklisted dimensions from general config<br/>
    
  * Sample Drill:<br/>
    * Core Sample:<br/>
      + Reworked code that manages rendering of a core sample texture<br/>
        + When there is an item in a vein instead of a block, it will paint sample as a cobblestone instead of stone to distinguish empty sample from a sample that contains only items<br/>
        + Fixed issue with no texture when trying to render more than one item<br/>
    
  * Arc Furnace:<br/>
    + Added config parameter *arcfurnace_electrodeAutoInserting* that allows electrode input to arc furnace from a top central block<br/>
    + Added config parameter *arcfurnace_legitSideInput* that disables side input of ores to arc furnace, leaving only top side with a hole for input<br/>
    + Added config parameter *arcfurnace_legitSideAdditive* that disables side input of additives to arc furnace, leaving only top side with a hole for input<br/>
    + Added config parameter *arcfurnace_legitSideElectrode* that disables side input of electrodes to arc furnace, leaving only top side with holes for input<br/>
    + Added config parameter *arcfurnace_legitSideOutput* that disables bottom and top sides output of products from arc furnace, leaving only side with a hole for output<br/>
    + Added config parameter *arcfurnace_legitSideSlag* that disables bottom side output of slag from arc furnace, leaving only side with a hole for output<br/>
    
  * Crusher:<br/>
    + Added config parameter *crusher_legitSideInput* that disables side input to crusher, leaving only top side of central top blocks for input
--------------------------------------------------

  Mineral Config Files

  Each json file inside IEMinerals folder contains list of minerals with the following structure:

  https://github.com/SealedSeal/ImmersiveEngineeringExcavated/blob/bf4d9b68614af2f3c6b7f9ac92d97fe9f69629b3/mineralsExample/default.json#L2C3-L25C4

  * name - Name of a mineral (String)
  * genType - Type of a mineral (String)
    * Three types available:
      + "infinite" - Unlimited yield
      + "fixed" - Fixed yield based on maxCapacity
      + "range" - Random yield between minCapacity and maxCapacity
  * minCapacity - Minimal capacity that can be generated if "range" type is selected (int)
  * maxCapacity - Maximal capacity that can be generated if "range" type is selected, also used as a value for "fixed" type (int)
  * mineralWeight - Weight of a mineral for its selection by a generator among other minerals (int)
  * failChance - Still have no idea what it is used for, probably somehow relates to excavator fail chance (float)
  * ores - List of resources that can be excavated (String[])
    * Can be blocks or items
    * Supports ore dictionary names, id names, and id names with metadata, examples:
      * "ironOre"
      * "minecraft:iron_ore"
      * "minecraft:stone/1"
  * chances - % of each resource from the ores list in a mineral, sums to 1 (float[])
  * blacklist - will not generate minerals in dimensions from list "dimensions" if set to true (boolean)
  * dimensions - List of dimensions where the mineral can or cannot be generated based on "blacklist" parameter (int[])

More examples of minerals with type "range"
https://github.com/SealedSeal/ImmersiveEngineeringExcavated/blob/master/mineralsExample/vanilla_nether.json

  
