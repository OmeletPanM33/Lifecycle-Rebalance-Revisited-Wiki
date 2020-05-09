This page describes the settings in the WG_CitizenEdit.xml file and what they do.  Any of these settings can be changed in your favourite XML or text editor.

The game will auto-generate a replacement settings file (with the mod default settings) if this file is missing or damaged.  If you want to reset to the defaults, simply delete the file.

## Travel
### Density
This section is broken down into low- and high- density sections, used for the residents of low- and high-density residential buildings (so people living in detached houses can have different travel preferences to those living in dense apartments, just like in real life).
### Wealth
Each of the density settings is in turn broken down into low-, medium-, and high-wealth sections, enabling different preferences depending upon wealth level.  Wealth is determined by the level of the residential building that the citizen lives in; level 1 is low-wealth, levels 2 and 3 are medium-wealth, and levels 4 and 5 are high-wealth.
### Age group
Finally, each wealth level is broken down into the five citizen age groups: child, teen, young (young adult), adult, and senior.  Each of these groups can be given its own transport preferences; for example, you may not want to see any children driving cars!
## Transport probabilities
The modifiers are for car, bike (bicycle), and taxi.  Each modifier is a percentage chance of taking that option when the game checks for it.  Note that these do NOT need to add up to 100%, and that there is no separate chance for walking or public transport - and that's due to how the game operates:

The game works by doing a probability check against each of the modes in order.  It will first check the probability of car travel; if car is not chosen, then it checks against the bicycle probability; if that isn't chosen, it checks taxi; and if that isn't taken then the citizen will walk or use public transport.

So, if you want to see a lot of walkers/public transport passengers, set the car, bike, and taxi probabilities low.

## Migrate
Currently unused.

## Lifespan
### modifier
Changing this will expand the lifespan of the people by this number. Integer values are accepted. Default is 2.

### survival
Each decile (10 years) of life has its own survival chance, defined as the percentage of the population entering that decile that will survive to the next decile.  Float values with no more than 3 decimal places are preferred

### sickness
Each decile (10 years) of life will have its own sickness chance.  It is defined as the percentage of the population entering that decile that will become sick by the next decile.  Float values with no more than 3 decimal places are preferred

### cheatHearse
When people die of old age, they have this percentage chance for their bodies to simply disappear (without requiring deathcare or hearse transport).  Set this value to 100 to avoid any need for deathcare or hearses due to deaths from old age.

**NOTE:** Deaths caused by events (including deaths from pollution) are not covered by this mechanic.