# Loop 3 Integration

xDrip4iOS can be used as an offline CGM data source for the FreeAPS fork of Loop

___
## What is Loop?

**Loop** is an **Artificial Pancreas System** (APS) written for the iPhone.

An APS works by reading blood glucose values, predicting/calculating the insulin requirement and automatically adjusting a user's insulin pump with the aim of keeping the user within their target blood glucose range.

While Loop 3 supports using Nightscout as a cgm data source, it requires constant internet access and depending on what glucose sources are used for input Using on-the-local-phone CGM access using Dexcom or xDrip4iOS (Dexcom G4/5/6 + Libre with some [limitations](../index.md#compatible-sensors)) does not require internet access and is thus a preferred method for looping.

Important: The Testflight version of xDrip4iOS **cannot** be used with FreeAPS. You must build xDrip4iOS from source.
___
## How do I install FreeAPS (Loop)?

The Loop and Learn repository is [here](https://github.com/loopnlearn/LoopWorkspace).

With the advent of iOS 15 (Xcode 13), all Loop and FreeAPS builds require using LoopWorkspace. LoopDocs has been modifed for workspace builds.  If you follow the directions for [LoopDocs: Build Loop App](https://loopkit.github.io/loopdocs/build/step14), when you get to the instruction where you choose what Loop to build, select FreeAPS instead of Loop Master.

Please read the [LoopDocs: Updating](https://loopkit.github.io/loopdocs/build/updating) page to ensure your Mac is fully updated (both MacOS and Xcode) and Xcode Command Line tools/Git are installed before proceeding.

Follow all instructions in LoopDocs for building the Loop app - the only difference is you to select FreeAPS instead of Loop when running the script in the terminal. 

Remember that xDrip4iOS is a separate app and must be [built from source](../install/build.md) in order to successfully interface with FreeAPS.

___
### Sign the Targets

As per a normal Loop build, you will need to sign the four targets using your Development Team.

Signing will automatically set the Bundle Identifier for your app. You can change this, but be aware that it will then install a completely new FreeAPS app. It's better to just leave it as is.
___
### App Group

Please do not modify the App Groups at all. This is important to ensure integration with xDrip4iOS.

___
## How do I install xDrip4iOS?

You need to follow the [Build From Source](../install/build.md) instructions.


The common LoopKit app group is already written into the standard project file in xDrip4iOS so no need to touch anything.

___
## Operation

The operation of both FreeAPS (Loop) and xDrip4iOS is the same. The only thing needed is to add a CGM in FreeAPS and chose "xDrip4iOS".

This will tell FreeAPS to look for glucose data in the shared app group via Julien's xdrip client.

</br>
