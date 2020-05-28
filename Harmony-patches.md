Lifecycle Rebalance Revisited currently uses [Harmony 1.2.0.1](https://github.com/pardeike/Harmony) to deploy the following patches:

# ResidentAI
### ResidentAI.GetCarProbability
_ushort instanceID, ref CitizenInstance citizenData, Citizen.AgeGroup ageGroup_

This is a **Prefix** patch with standard priority that **preempts** the original method (returns **false** from the Prefix method).

This patch is dynamically applied (or unapplied) depending on user settings, and implements the mod's changed transport preferences.

### ResidentAI.GetBikeProbability
_ushort instanceID, ref CitizenInstance citizenData, Citizen.AgeGroup ageGroup_

This is a **Prefix** patch with standard priority that **preempts** the original method (returns **false** from the Prefix method).

This patch is dynamically applied (or unapplied) depending on user settings, and implements the mod's changed transport preferences.

### ResidentAI.GetTaxiProbability
_ushort instanceID, ref CitizenInstance citizenData, Citizen.AgeGroup ageGroup_

This is a **Prefix** patch with standard priority that **preempts** the original method (returns **false** from the Prefix method).

This patch is dynamically applied (or unapplied) depending on user settings, and implements the mod's changed transport preferences.

### ResidentAI.CanMakeBabies
_ushort instanceID, ref CitizenInstance citizenData, Citizen.AgeGroup ageGroup_

This is a **Prefix** patch with standard priority that **preempts** the original method (returns **false** from the Prefix method).

It is always applied when the mod is running and implements a minor fix to have babies only produceable by adult females.

### ResidentAI.UpdateAge
_uint citizenID, ref Citizen data_

This is a **Prefix** patch with standard priority that **preempts** the original method (returns **false** from the Prefix method).

It is always applied when the mod is running, and is **critical** to the operation of the mod; it implements all the lifecycle (mortality, sickness, deathcare) settings.

This patch also uses reverse redirects to access game instances of FinishSchoolOrWork and Die methods.

### ResidentAI.UpdateHealth
_uint citizenID, ref Citizen data_

This is a **Transpiler** patch that implement's the mod's deathcare transportation probabilities for citizens who die from illness.

This patch replaces the code that calculates the base game's chance of a deceased citizen being released (instead of requiring deathcare transportation) with a call to this mod's deathcare transportation policy instead.  The exact C# code changed is near the end of the method and is the line immediately after the call to Die(citizenID, ref data):

`if (Singleton<SimulationManager>.instance.m_randomizer.Int32(2u) == 0)`

# Citizen
### Citizen.GetAgeGroup
_uint citizenID, ref Citizen data_

This is a **Prefix** patch with standard priority that **preempts** the original method (returns **false** from the Prefix method).

It is applied when the 'Custom Retirement Age' is option is active, and is unapplied when not in use (this includes when this option is changed during gameplay).  Not having this patch applied when custom retirement ages are in play will break a lot of things regarding seniors and retirement.

# OutsideConnectionAI
### StartConnectionTransferImpl
_ushort buildingID, ref Building data, TransferManager.TransferReason material, TransferManager.TransferOffer offer, int touristFactor0, int touristFactor1, int touristFactor2_

This is a **Transpiler** patch with standard priority.  It replaces a single block of code in the middle of the method with a call to a custom method containing code which implements the mod's changes to immigrants (randomisation of ages and education levels).
