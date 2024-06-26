# ActionScript 3 Extension for Panic's Nova

Extension for ActionScript 3 and MXML in [Panic's Nova](https://nova.app/) using [Bowler Hat's AS3MXML](https://github.com/BowlerHatLLC/vscode-as3mxml) as an LSP (which only works if there's an `asconfig.json` in the directory).
And uses Panic Nova's tasks cleaning/building/running.

More details about AS3MXML are in the [as3mxml.novaextension README.md](as3mxml.novaextension/README.md)

Currently a work in progress. Issues work, and some features like Jump to Definition work occasionally.

# Syntax check

The syntax provided with the AS3MXML is not to Nova's liking and doesn't fully recognize things, need to reworked.

I stared working on using the Syntax XML from Panic's Javascript extensions, and have made a bit of progress.

* May need to check variable names. Think JS doesn't allow $ in the name, but AS3 does

## Notes

About [AIR Building](https://help.adobe.com/en_US/air/build/index.html)

About [AIR ADL command line](https://help.adobe.com/en_US/air/build/WSfffb011ac560372f-6fa6d7e0128cca93d31-8000.html)

## FlashBuilder migration

The [Pure JavaScript XML (pjxml)](https://github.com/smeans/pjxml) is used to help migrate some of the FlashBuilder setting to Nova.

May be switching to a modified version of [alabianca/xml-to-json](https://github.com/alabianca/xml-to-json) or [recalcitrantQ/xml-to-json](https://github.com/recalcitrantQ/xml-to-json/commits/master/) to handle the XML to JSON.
The Pure JavaScript XML sometimes fails on mobile project that may have multiple build targets

A lot of the settings from Flash Builder will be imported to the workspace's settings.

**@TODO**
 * Import Flash Builder project when opening the first time.
 * Try to automatically add a task to the project (based on AIR/Mobile/Web)

For now, you need to manually add a Task, and then run the command from the menu command will log to console what the settings should be.

### .flexProperties

Only using this to set if the project's Default Syntax is either MXML or ActionScript 3.

### .actionScriptProperties

Used to grab some things used for a task like:

 * Main application path
 * Source dirs
 * Lib dirs
 * Additional compiler args

### .flexLibProperties

Not read yet.

### .project

It will read this and rename the Nova project to the same name as the FlashBuilder project.

@TODO: If there is a tag of `<linkedResources>` with a `<type>` of 2, then warn the user that these types of links are not supported.
