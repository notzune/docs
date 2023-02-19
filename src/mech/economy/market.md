> <span style="color:red">Currently unimplemented.</span>
# Market

The market system is one of the key features of the entire project as it serves as the backbone of the economy. Caution must be used when designing, discussing, or working on features of the economy in general and the market system in particular. Measures need to be taken to ensure the system can not be gamed or at least the gaming of the system will be kept to a minimum. With a proper dynamic economy, we can avoid players finding METAs that break the economy.
## Overview
There will be two parts to the market. The **global** and the **local** market. 

The **global market** determines things on a server-wide scale, such as a price ceiling to set the default cost of items put on sale on the market if not specified by the user. It also creates an index on the webserver as a reference for players to be able to see a [spreadsheet](economy/spreadsheet.md) of the current market prices of items. The global market is meant to be a guideline to building the local markets but should not be limited to the end user in any real way.

The **local market** determines the prices and sale of goods on a [region](../../map/regions.md) basis. Much like the **global market**, the local market sets price ceilings on items and uses the global market prices to set the maximum initial price on items. The local market also records how many unique vendors sell a certain item in that region and inversely raises the price ceiling to allow players a chance to be able to corner the market in that specific region.

## The Global Market
The **global market** monitors the **supply** of items server-wide. Supply is the number of items submitted to chests connected to a vendor/merchant [NPC](NPCs/types/merchants.md). This keeps track of the **global supply** of items. As the supply increases, the global price cap lowers, which in turn will lower the global default initial pricing of items. 

An initial price point is required due to the hyperbolic formula used in determining dynamic market prices. It would be impossible to buy any item if it reaches 0.    

### Inflation
The initial price point (after it is first configured by an Administrator via the configuration file) is affected by in-game inflation rates using the formula:

``R = ((B - A)/A) x 100``
> Where A = starting cost; B = ending cost; R = inflation rate
   
How it works: It takes the pre-configured initial price point for an item (B) and after a month(?) compares it with the mean price point of that specific item across all of the registered local markets (A). The resulting rate (R) is then subtracted from the starting price point (A) and the new market month begins.

## The Local Market (Per-region Markets)

The **local market** is where the really interesting part begins. The local market, like the **global market** sets an initial price on items based on two factors:   

The first factor is the global market's initial price. The local market's initial price cap should always either equal or be less than the global market's. 

By default, all items start in initial pricing mode. Initial pricing is a temporary price cap or ceiling that keeps prices low until a reasonable amount of the item has been sold to the shop. The price of an item will not change while it is in dynamic pricing mode.    

Due to the nature of the pricing formula, an item with 0 stock has an infinite sell value when in dynamic pricing mode. Initial pricing is there to fix this issue. Tradeable objects will automatically switch to dynamic pricing mode whenever the dynamic price is less than the initial price. 

## Dynamic Pricing
The main purpose of this economic system is to allow for dynamic price changes in the server's economy in order to prevent stagnant gameplay and force players to constantly adapt to market prices instead of abusing a singular trading META.

Dynamic pricing mode will automatically be activated for all items once they reach a certain stock level. Once in dynamic mode, the price of the item will vary depending on how much stock is available for that item.    

As the stock approaches 0, the price will approach infinity, and as the stock approaches infinity, the price will approach 0. This means that it is essentially impossible to purchase the final item in a shop whenever it is in dynamic pricing mode. The pricing formula is as follows: 

``price = (median * value) / stock.`` 

## Taxation
This economic system will allow for different forms of taxation. Taxes, by default, are deposited into the region's bank account unless an eligible bank account is found. 
```
         ┌───────────────┐
         │Collected Taxes│
         └──────┬────────┘
                │
                │
                │
                ▼
      ┌──────────────────────┐
      │                      │
      │ Available town bank? │
      │                      │
      └─────────┬────────────┘
                │
                │
                ▼
     ┌────────────────────────┐
     │                        │
     │ Available nation bank? │
     │                        │
     └──────────┬─────────────┘
                │
                │
                │
                ▼
      ┌──────────────────────┐
      │                      │
      │  Region bank account │
      │                      │
      └──────────────────────┘
```

> 📝 **Note:** Here is a chart showing the priority hierarchy of where the taxes are deposited.    

Tax rates default to whatever is defined in the ``config.yml`` to be the "global tax rate", but if a shop is within the territory of a town or nation and they have set its tax rate, then it will use that rate instead. If both the town and the nation set a tax rate, it would take the average of both numbers.

### Purchase Tax

Purchase tax is applied when items are purchased in dynamic pricing mode. If the tax rate were 3%, the tax charged for the purchase would be 3% of the purchase price.

### Initial Tax
Initial tax is applied when items are purchased in initial pricing mode. It works just like a purchase tax.

### Enchantment Tax

Enchantment tax is applied when enchantments are purchased. Enchantment tax will apply to all enchantments unless they are in static pricing mode.
### Dynamic Sales Tax

It allows poor players to make more money during sales than rich players. Dynamic tax will only be applied when the player's balance is between the money-floor and the money-cap defined in config.yml. The maximum tax rate defined in config.yml will be applied when the player's balance is equal to or greater than the money-cap. If the max tax is set to 100 percent the player will no longer make money when selling items to a server shop. At the money floor, no tax will be applied. Between the cap and floor, the tax rate will gradually increase as the player's balance approaches the money cap.

> See also [Banking](banking.md), and the [Nation System](../nation-system.md)    
   
## Object Hierarchy
In this section we will cover the object hierarchy of how the actual code will be structured as well as snippets from [Gringotts](https://github.com/nikosgram/gringotts), [HyperConomyX](https://github.com/coleweinman/HyperConomyX) and [TownyEco](https://github.com/ZackRuybal/TownyEco) as a sort-of guideline for how the plugin will work once completed.    

