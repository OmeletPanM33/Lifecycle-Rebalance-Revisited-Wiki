# Brief overview
Once the game has decided that a citizen wants to travel to a destination, it looks at a range of issues to determine if the cim is going to walk, try public transport, or get a vehicle.

If the cim tries to get a vehicle, the game then queries a subroutine to get the specific probabilites (out of 100) for car usage, bike usage, and taxi usage (in that order).  These probabilities do not need to sum to 100, as the game checks each probability individually.

This part (the percentage chance for each transport mode that's returned to the part of the game that makes that query) is what this mod changes.

Note that the Tourist AI has it's own implementation of these probabilites, which this mod doesn't touch (this mod only patches Resident AI).

If the probability for one of those is met, then that's the vehicle the citizen will try to use. If no vehicle ends up being selected, and there's no viable walking/public transport option, or if pathfinding fails (e.g. if there's no connected road), then the travel attempt will simply fail and the cim won't go anywhere (and won't be instantiated as a 'visible' travelling cim for this attempt). 

# Mod changes
This mod simply changes the results of the queries the game makes to determine the probability of each mode of transport for that citizen.  The final decision of transport mode is then made by the game, based on the probabilities provided.

The relevant methods patched by this mod are:
* [`ResidentAI.GetCarProbability`](https://github.com/algernon-A/Lifecycle-Rebalance-Revisited/wiki/Harmony-patches#residentaigetcarprobability)
* [`ResidentAI.GetBikeProbability`](https://github.com/algernon-A/Lifecycle-Rebalance-Revisited/wiki/Harmony-patches#residentaigetbikeprobability)
* [`ResidentAI.GetTaxiProbability`](https://github.com/algernon-A/Lifecycle-Rebalance-Revisited/wiki/Harmony-patches#residentaigettaxiprobability)

This mod doesn't do anything else other than to change those probabilities.  In particular, this mod does **NOT** affect the determination of when and where a citizen travels, or if a citizen decides to walk or take public transport before a vehicle check is made, or any route selection or pathfinding.

# Vanilla behaviour
For each agegroup (child/teen/young adult/adult/senior), the base game always returns probabilities of:
* For cars, 0/5/15/20/10
* For bikes, 40/30/20/10/0 (plus 10 to each chance if the cim lives in a building covered by the 'Encourage Biking' policy)
* For taxis, 0/2/2/4/6

These probabilities are duplicated by the 'WG_GameDefaults.xml' [alternative configuration file](https://github.com/algernon-A/Lifecycle-Rebalance-Revisited/wiki/Included-alternative-configuration-files) packaged with this mod.

## Tourists
Tourists always have a 20% chance for any transport probability choice, with no breakdowns based on age (which is why you sometimes see tourist children driving cars).