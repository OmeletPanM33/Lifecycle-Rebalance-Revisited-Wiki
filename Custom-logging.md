In addition to the standard logging to the output_log.txt, Lifecyle Rebalance Revisited offers the option of detailed custom logging about the actions the mod is taking.

The options to activate (or deactivate) these logs can be found at the bottom of the mod's in-game options panel.  Each logging option can be activated or deactivated independently of the others.

When activated, each option will log its activity to the specified text file in your local settings directory (see the [configuration files](https://github.com/algernon-A/Lifecycle-Rebalance-Revisited/wiki/Configuration-files) page for details on where this is for your operating system).  If the relevant file doesn't already exist, it will be created automatically; if it already exists, the output will be appended to the end of the file.

Currently, four detailed custom logs are available, and each has a unique log filename:
* **Death logging**: Lifecycle death log.txt
* **Immigration logging** Lifecycle immigration log.txt
* **Transportation choices logging** Lifecycle transport log.txt
* **Sickness logging** Lifecycle sickness log.txt

Note that these logs only capture actions performed by this mod.  Actions performed by the base game or by other mods are not included.

### Death logging
Records the citizen's age at death for every death caused by this mod (natural ageing).  Note that it doesn't record deaths NOT caused by this mod (those with 'special causes, e.g. pollution or natural disasters).

### Immigration logging
Records the age, family, and education level of every immigrant whose attributes have been selected by this mod.

### Transportation logging
Records the result of every transport mode query made by citizens to this mod.

**NOTE**: Transportation logging generates a huge amount of data and will cause your game to pause slightly every few seconds as it writes this data to disk.  This option is not recommended for general gameplay.

### Sickness logging
Records every citizen made sick by this mod along with the 'chance factor' that was applied to that selection.

The chance factor is the chance out of 100,000 for the citizen to become sick out of each year of ageing (which is the % sickness chance in the settings divided by 35 if using default calculations or 25 if using legacy calculations; see the [theory of operation](https://github.com/algernon-A/Lifecycle-Rebalance-Revisited/wiki/Lifecycle-calculations:-theory-of-operation#sickness) page for more details).

**NOTE**: This log does **NOT **include sicknesses not caused by this mod, e.g. by pollution or noise.
