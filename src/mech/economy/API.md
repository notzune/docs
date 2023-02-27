# API
The API portion of the Market system is used to hook all of the subsequent mechanics such as but not limited to the [Cults](../cults.md) system, [Nations](../nodes.md) system, and the [Quests](../quests.md) system.   

The Market API acts as an intermediary between consumer and provider plugins on the server, by allowing them to easily hook together using our API.

Provider plugins are those which offer a service within the server. Example providers would be something such as `LuckPerms` (permissions), `TheNewEconomy` (economy), and `VentureChat` (chat). Consumer plugins are those which utilize a provider plugin, such as `JobsReborn` (economy consumer).

## Why not use [insert name here] economy plugin?
There are various economy APIs already on the market such as Vault and, recently, Treasury (which we have been influenced heavily by) however these APIs are designed for wide use by the public. Therefore they are designed to fill a wide range of general purposes without any specialization for more niche or specific specialized use cases such as those that may arise with the nature of something like this project.   

[Vault](https://github.com/MilkBowl/VaultAPI) served as (and currently still serving as) the leading Economy API for more than a decade now. However, that plugin hasn't been updated for the past several years besides simple maintenance updates and introduces no new features. It provides no support for something such as multiple currencies (i.e. *John has 9 coins and 4 tokens*), transactional history, more verbose economy responses (Vault simply states that a transaction has failed without providing a reason as to why it failed), or even transaction events.

[Treasury](https://github.com/ArcanePlugins/Treasury/wiki/About-Treasury) is a more recent API that hit the market at the start of 2022 and is (at the time of writing this page) currently going through a massive rewrite that has resulted in it being mostly unusable in its current state. However, it addresses a lot of the issues with Vault that were listed above. Our API is modeled heavily after Treasury which is reflected in the proposed [hierarchy](api/hierarchy.md).    

