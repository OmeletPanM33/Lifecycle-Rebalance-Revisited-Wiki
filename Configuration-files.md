# Main XML configuration file (WG_CitizenEdit.xml)
Lifecycle Rebalance Revisited currently (still) uses the same XML configuration file as the Citizen Lifecycle Rebalance mod.  It natively uses version 2 of the file format, but can still read earlier versions.  This means that any existing Citizen Lifecycle Rebalance settings will be read automatically by Lifecycle Rebalance Revisited without anything needing to be done by the user.

The configuration file is an XML file called 'WG_CitizenEdit.xml'.  If no file already exists, one with the default configuration will be automatically created by the mod on the first game load after activation.  This file resides in local settings directory, which can be found in the following locations:

## Location by OS
Windows = C:\Users\<username>\AppData\Local\Colossal Order\Cities_Skylines
Mac = /Users/<username>/Library/Application Support/Colossal Order/Cities_Skylines
Linux = /home/<username>/.local/share/Colossal Order/Cities_Skylines

Changed values in the file will be seen on loading a different city or loading from the main menu.  The file is updated on each load and written-back by the mod with the updated settings.  A backup file with the previous settings (WG_CitizenEdit.xmlk.bak) is also automatically created in the same location.

Some values in this file can be changed (without having to edit the XML directly) by using the in-game mod options panel.  Changes made via this method will also take place immediately in game as soon as the relevant 'Save' button is pressed.

# Lifecycle Rebalance Revisited configuration file (LifecycleRebalance.xml)
An additional configuration file called 'LifecycleRebalance.xml' resides in the main application directory (in Windows, Steam\steamppas\common\Cities_Skylines).  This file contains settings added in Lifecycle Rebalance Revisited for features that aren't available in the original mod, such as calculation mode selections and retirement age options.  This file shouldn't be edited manually; instead, use the in-game mod options panel,