This describes the function of the citizen ageing code found in ResidentAI.UpdateAge(uint citizenID, ref Citizen data)

### General notes
* Cim health (m_health), is clamped between 0 and 100 - see ResidentAI.UpdateHealth(uint citizenID, ref Citizen data).
* Cim wellbeing (m_wellbeing), is clamped between 0 and 100 - see ResidentAI.UpdateWellbeing(uint citizenID, ref Citizen data).
* A 'full life' for statistical purposes as defined by the game is at age 240.

## Base game


* Number 1 is set to the cim's age +1.
* Number 2 is set at 240, number 3 at 255.
* Number 4 is calculated thus: invert the health percentage (m_health), multiply by 3, then subtract from 145.
* A cim with full health will end up with 145, a cim with less than 51.6667 health will end up with 0 (minimum bound).
* Number 2 is then increased by one-third of number 4 (so a cim with full health ends up with 288.333; poor health, 240).
* Number 3 is then increased by number 4 (so a cim with full health ends up with 400; poor health, 255).
* A 'random death chance' flag is then calculated (for cims who are stationary and not in vehicles) of 0.15% (3 / 2000).

After this, a random number is generated between number 2 and number 3 (specifically number 2 * 100 and number 3 * 100, then the result divided by 100, to reduce rounding biases).  A cim with full health will end up with a figure in the range of 288.333-400.0; a cim with poor health, 240-255.

If this random number is less than or equal to the cim's age plus 1 (number 1), OR the random death chance flag is set, then the cim dies.

If the cim dies, an integer random number from 0 to 2 is generated; if this is zero, then the corpse 'disappears' (doesn't need deathcare).

## Legacy mod calculations
A modifier based on m_health and m_wellbeing is generated: 90,000 plus (150 * health ) plus (50 * wellbeing).  This gives a number between 90,000 and 110,000.

The cim's survival probability, via the DataStore from the configuration file, is derived from the probability in the configuration file thus: 100,000 - (100,000 * (1 + ln(probability) / 25))

With default settings, for somebody in the final decile, this is 16,150.  Second-final decile, this is 8,548.  Third-final, 2,704. Fourth-final, 789.  Second decile is 7 (lowest value).

A random number is generated between 0 and the modifier.  If this is less than the survival probability, the cim dies.

If the cim dies, an integer random number from 0 to 99is generated; if this is less than the chance set in the Datastore, then the corpse 'disappears' (doesn't need deathcare).