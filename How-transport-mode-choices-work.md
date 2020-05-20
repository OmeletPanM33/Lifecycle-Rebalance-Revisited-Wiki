# Brief overview
Once the game has decided that the cim will be moving, it looks at a range of issues to determine if the cim is going to walk, try public transport, or get a vehicle.

If the cim tries to get a vehicle, the game then queries a subroutine to get the specific probabilites (out of 100) for car usage, bike usage, and taxi usage (in that order).  Note that these probabilities do not need to sum to 100; the game checks each probability individually.

This part (the % chance for each transport mode that's returned to the part of the game that makes that query) is what this mod changes.

If the probability for one of those is met, then that's the vehicle the cim will try to use. If no vehicle ends up being selected, and there's no viable walking/public transport option, or if pathfinding fails (e.g. if there's no connected road), then the travel attempt will simply fail and the cim won't go anywhere (and won't be instantiated as a 'visible' travelling cim for this attempt). 

Note that the Tourist AI has it's own implementation of these probabilites, which this mod doesn't touch (this mod only patches Resident AI).

# Mod changes
This mod simply changes the results of the queries the game makes to determine the probability of each mode of transport for that citizen (these queries are the method calls to ResidentAI.GetCarProbability(), ResidentAI.GetBikeProbability(), ResidentAI.GetTaxiProbability()).  Nothing else is affected.

In particular, this mod does NOT affect the determination of when and where a citizen travels, or if a citizen decides to walk or take public transport before a vehicle check is made, or any route selection or pathfinding.  This mod doesn't even make the final transport choice; it merely returns the probabilities, and the game makes the final decision.

# Vanilla behaviour
For each agegroup (child/teen/young adult/adult/senior), the base game always returns car probabilities of 0/5/15/20/10, bike probabilities of 40/30/20/10/0 (plus 10 to each chance if the cim lives in a building covered by the 'Encourage Biking' policy), and taxi probabilities of 0/2/2/4/6

These probabilities are duplicated by the 'WG_GameDefaults.xml' alternative configuration file packaged with this mod.

## Tourists
Tourists always have a 20% chance for any transport probability choice, with no breakdowns based on age (which is why you sometimes see tourist children driving cars).

If it is just normal transport preferences, then it's just the mod doing exactly what it says it does (and can easily be changed).

All this mod does is change the results of when the game asks what mode of transport the citizen wants to use. The game determines when and where a citizen travels, seeks input from transport choice routines, then decides the method of travel, then conducts pathfinding. The only part this mod touches in all of that is the transport choice routines (it doesn't even get to make the final decision on transport mode, just gives the probabilities to the game for it to decide). 