> <span style="color:red">Currently unimplemented.</span>
# Market

The market system is the backbone of the economy. 
## Overview
There will be two parts to the market. The **global** and the **local** market. 

The **global market** determines things on a server-wide scale such as price ceiling to set the default cost of items put on sale on the market if not specificed by the user. It also creates an index on the webserver as a reference for players to be able to see a [spreadsheet](economy/spreadsheet.md) of the current market prices of items. The global market is meant to be a guideline to build the local markets but should not be limiting to the end user in any real way.

The **local market** determines prices and sale of goods on a [region](../../map/regions.md) basis. Much like the **global market**, the local market sets priece ceilings on items and uses the global market prices to set the minimum price on items. The local market also records how many unique vendors sell a certain item in that region and inversely raises the price ceiling to allow players a chance to be able to corner the market in that specific region.

## The Global Market
The global market price system takes two variables: The default start price as defined by the server (A) and the number of items recorded in the **global supply** (B).

The **glohal market** monitors the **supply** of items server-wide. Supply is the amount of items submitted to chests connected to a vendor/merchant [NPC](npcs/types/merchants.md). This keeps track of the **global supply** of items. As the supply increases the global price cap lowers which in turn will lower the global default price of items. 

## The Local Market (Per-region Markets)