# Weapon Asset Pack
A resource mod for Owlcat's Rogue Trader cRPG. Provides a collection of custom weapon prefabs that can be externally referenced by 3rd party RT mods.

<p align="center"><img src="Images/Splash.jpg?raw=true" width="600" height="250"/></p>

## Overview
This mod adds a selection of custom weapon prefabs that mod authors can reference in their own blueprints without needing to add the content to their own mod. A selection of ranged and melee weapons are available, which will be expanded over time.

Mod users will need to install this mod alongside whatever 3rd party mods they want that reference its assets. This mod does not add any content to the game directly by itself.

## Installation
### For endusers:
This is an Owlmod, made using the Unity template supplied by Owlcat. In order to properly load custom assets, you ***must*** install the Unity Mod Manager-based mod [MicroPatches](https://github.com/microsoftenator2022/MicroPatches/releases) by microsoftenator2022. You can install it manually or via [ModFinder RT](https://www.nexusmods.com/warhammer40kroguetrader/mods/146).

Use [ModFinder RT](https://www.nexusmods.com/warhammer40kroguetrader/mods/146) to install this mod automagically.

Alternatively, to install the mod manually, first make sure you have run the game at least once. Download the mod from [Nexus](https://www.nexusmods.com/warhammer40kroguetrader/mods/???) and extract it into:

`%userprofile%\AppData\LocalLow\Owlcat Games\Warhammer 40000 Rogue Trader\Modifications\`

Each Owlmod needs to be in its own sub-folder in the Modifications folder.

Afterwards, you'll need to edit OwlcatModificationManagerSettings.json in the base Warhammer 40000 Rogue Trader folder in a text editor (Notepad++ recommended). It should look something like this:

```
{
"$id": "1",
"SourceDirectories": [],
"EnabledModifications": ["DPWeaponAssetPack"],
"ActiveModifications": ["DPWeaponAssetPack"],
"DisabledModifications": []
}
```

If you have other mods, list them in quotes separated by commas. For example:

```
"EnabledModifications": ["DPWeaponAssetPack", "ModName2", "ModName3"],
"ActiveModifications": ["DPWeaponAssetPack", "ModName2", "ModName3"],
```

You can move individual mods from the ActiveModifications section to the DisabledModifications section if you want to disable them without physically removing them.

### For Mod Authors:
Ensure you have the mod template prepared ([refer to the initial setup guide](https://github.com/WittleWolfie/OwlcatModdingWiki/wiki/Initial-Setup-of-v1.5-Rogue-Trader-Template)) and that you have installed the template component of [MicroPatches](https://github.com/microsoftenator2022/MicroPatches/releases) (MicroPatches-Editor-Installer.exe).

Download a copy of the asset pack's mod folder from the [releases section](https://github.com/DarthParametric/DPWeaponAssetPack/releases/latest) and extract it to `WhRtModTemplate\Assets\Modifications\` alongside your existing mod project/s.

Download the edited copies of the [ExtractBlueprintDirectReferences.cs](Scripts/ExtractBlueprintDirectReferences.cs) and [PrepareBundles.cs](Scripts/PrepareBundles.cs) template scripts. Place them into the template folder's `WhRtModTemplate\Assets\Editor\Build\Tasks\` folder, overwriting the originals when asked.

Create your own mod project, if you haven't already. Create a new weapon blueprint and under the `m_VisualParameters` section, click the browse button next to the `m_WeaponModel` slot to choose the appropriate weapon prefab from the asset pack. You can also do the same for icons. Once the blueprint has been edited to your requirements, add it to your mod's Blueprint folder. 

**N.B.:** Make sure you do ***not*** physically include any of the asset pack's content in your own mod folder! Your mod only requires blueprint references. Endusers will need to download the mod version of the asset pack separately. 

If you are manually editing blueprints rather than using the template, refer to the [GUID reference sheet](Asset_GUID_Reference_Sheet.md) for the values to use.

While not strictly necessary, it is suggested that you add the asset pack's ID (DPWeaponAssetPack) to your mod's dependency list. This will ensure that ModFinder will flag it as required when users install your mod.

## Known Issues
There are numerous issues with hand positioning and (excessive) wrist rotation across multiple animations and weapon types. This is a vanilla issue. In practice you'll never see it due to the isometric camera position. But it makes taking close-up screenshots _really_ annoying.

## Acknowledgements
Many thanks to the modders on the Owlcat Discord, but particularly Kurufinve, microsoftenator2022, and ADDB for helping to coach me through my ineptitude in order to get the mod working. Thanks to thehambeard for the port of Cinematic Unity Explorer and troubleshooting issues with the dollroom in my attempts to get decent screenshots.
