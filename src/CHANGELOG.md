# Changelog

All notable changes to this project will be documented in this file. This includes new features in-game such as plugins or mechanics, changes to existing features, plugins, mechanics, or additions/removals to the backend or frontend of the website or databases involved in the project. 

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [v2.1.0] - 2023-1-2 - 2023-1-23
### Added 
- Web
  - Seperate repositories for better version control via git
    - Created seperate repo to hold the documentation.
    - Created seperate repo for homepage
  - Started work on ``/craftviewer`` and ``/market``

- Discord
  - In process of creating seperate Discord server exclusively for developmental purposes.
  - Arya
    - Creation of seperate repository for Arya's core module for better version controlling
    - 

- Server
  - Upgraded server hardware to 6 cores and 16 GB RAM
  - Set up ``rdiff-backup`` in-order to periodically backup the map
  - Pruned uneccesary/redundant testing environments

- Map
  - Began work on "Port Xile" as well as plotting out the starting point for "Bettesville"   
  
  - "Port Xile"
    - Market area completed, needs polishing/decorating
    - Social area half finished, feels empty atm
    - Main fortress near complete needs interior/rooms
    - Residential area near complete, needs a few more blocks to fill out space as well as creation of a "high end" district

### Changed
- Misc
  - Fixed project version to display ``v2`` instead of ``v0``.

- Docs
  - Restructuring of the documentation
  - Creation of user guides
  - Began writing of the project overview

### Removed
- Web
  - Documentation and homepage from main web repository, moved to seperate repo
  - Configured Dynmap 
    - To use external webserver instead of the default internal webserver
    - Installed LiveAtlas UI
    - New link: [https://airshipcraft.tk/map](https://airshipcraft.tk/map)

- Discord
  - Moved ``core`` module of Arya to seperate repository