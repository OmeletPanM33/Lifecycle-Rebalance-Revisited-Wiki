Lifecycle Rebalance Revisited currently uses Harmony 1.2.0.1 to deploy the following patches:
### ResidentAI.GetCarProbability
ushort instanceID, ref CitizenInstance citizenData, Citizen.AgeGroup ageGroup

This is a **Prefix** patch with standard priority that preempts the original method (returns **false** from the Prefix method). It is always applied when the mod is running and implements the mod's changed transport preferences.

### ResidentAI.GetBikeProbability
ushort instanceID, ref CitizenInstance citizenData, Citizen.AgeGroup ageGroup

This is a **Prefix** patch with standard priority that preempts the original method (returns **false** from the Prefix method).  It is always applied when the mod is running and implements the mod's changed transport preferences.

### ResidentAI.GetTaxiProbability
ushort instanceID, ref CitizenInstance citizenData, Citizen.AgeGroup ageGroup

This is a **Prefix** patch with standard priority that preempts the original method (returns **false** from the Prefix method).  It is always applied when the mod is running and implements the mod's changed transport preferences.

### ResidentAI.CanMakeBabies
ushort instanceID, ref CitizenInstance citizenData, Citizen.AgeGroup ageGroup

This is a **Prefix** patch with standard priority that preempts the original method (returns **false** from the Prefix method).  It is always applied when the mod is running and implements a minor fix to have babies only produceable by adult females.

### ResidentAI.UpdateAge
uint citizenID, ref Citizen data

This is a **Prefix** patch with standard priority that preempts the original method (returns **false** from the Prefix method).  It is always applied when the mod is running, and is critical to the operation of the mod; it implements all the lifecycle (mortality, sickness, deathcare) settings.

It also calls its own private implementation of FinishSchoolOrWork(uint citizenID, ref Citizen data); when this mod migrates to Harmony 2.0 this private implementation will be replaced with a Reverse Redirect to the base method.

### Citizen.GetAgeGroup
uint citizenID, ref Citizen data

This is a **Prefix** patch with standard priority that preempts the original method (returns **false** from the Prefix method).  It is applied when the 'Custom Retirement Age' is option is active, and is unapplied when not in use (this includes when this option is changed during gameplay).  Not having this patch applied when custom retirement ages are in play will break a lot of things regarding seniors and retirement.


