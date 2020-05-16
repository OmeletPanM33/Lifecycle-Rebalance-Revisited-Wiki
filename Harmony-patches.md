Lifecycle Rebalance Revisited currently uses [Harmony 1.2.0.1](https://github.com/pardeike/Harmony) to deploy the following patches:

# ResidentAI
### ResidentAI.GetCarProbability
_ushort instanceID, ref CitizenInstance citizenData, Citizen.AgeGroup ageGrou_p

This is a **Prefix** patch with standard priority that **preempts** the original method (returns **false** from the Prefix method).

It is always applied when the mod is running and implements the mod's changed transport preferences.

**1.4 BETA changes**: patch is dynamically applied (or unapplied) depending on user settings.

### ResidentAI.GetBikeProbability
_ushort instanceID, ref CitizenInstance citizenData, Citizen.AgeGroup ageGroup_

This is a **Prefix** patch with standard priority that **preempts** the original method (returns **false** from the Prefix method).

It is always applied when the mod is running and implements the mod's changed transport preferences.

**1.4 BETA changes**: patch is dynamically applied (or unapplied) depending on user settings.

### ResidentAI.GetTaxiProbability
_ushort instanceID, ref CitizenInstance citizenData, Citizen.AgeGroup ageGroup_

This is a **Prefix** patch with standard priority that **preempts** the original method (returns **false** from the Prefix method).

It is always applied when the mod is running and implements the mod's changed transport preferences.

### ResidentAI.CanMakeBabies
_ushort instanceID, ref CitizenInstance citizenData, Citizen.AgeGroup ageGroup_

This is a **Prefix** patch with standard priority that **preempts** the original method (returns **false** from the Prefix method).

It is always applied when the mod is running and implements a minor fix to have babies only produceable by adult females.

**1.4 BETA changes**: patch is dynamically applied (or unapplied) depending on user settings.

### ResidentAI.UpdateAge
_uint citizenID, ref Citizen data_

This is a **Prefix** patch with standard priority that **preempts** the original method (returns **false** from the Prefix method).

It is always applied when the mod is running, and is **critical** to the operation of the mod; it implements all the lifecycle (mortality, sickness, deathcare) settings.

It currently calls its own private implementations of FinishSchoolOrWork(uint citizenID, ref Citizen data) and Die(uint citizenID, ref Citizen data); when this mod migrates to Harmony 2.0 these private implementations will be replaced with a Reverse Redirect to the base method (possibly with a Postfix to Die to implement the custom logging currently contained in the private implementation).

**1.4 BETA changes**: patch uses reverse redirects to access game instances of FinishSchoolOrWork and Die methods.

# Citizen
### Citizen.GetAgeGroup
_uint citizenID, ref Citizen data_

This is a **Prefix** patch with standard priority that **preempts** the original method (returns **false** from the Prefix method).

It is applied when the 'Custom Retirement Age' is option is active, and is unapplied when not in use (this includes when this option is changed during gameplay).  Not having this patch applied when custom retirement ages are in play will break a lot of things regarding seniors and retirement.

# OutsideConnectionAI
### StartConnectionTransferImpl
_ushort buildingID, ref Building data, TransferManager.TransferReason material, TransferManager.TransferOffer offer, int touristFactor0, int touristFactor1, int touristFactor2_

This is a **Prefix** patch with standard priority but after **connection.outside.advanced** that **preempts** the original method (returns **false** from the Prefix method).

Following **connection.outside.advanced** enables the AdvancedOutsideConnection Prefix patch to execute first to set up its tourist factor changes, as there's no conflict between that mod and this mod's patches.

Currently, this Prefix patch re-implements the entire original method with the patch itself in the middle.  Obviously, this is less than ideal, and is a remnant of the original migration from the WG Detours implementation to Harmony.  A replacement Transpiler patch is currently in development.

**1.4 BETA changes**: patch converted to Transpiler.
