---
layout: main
title: Installation.
description: instructions and binaries
---
# How Do I start?

`Arrigo Local` needs `EXO2019 Edition 3` to run. 

> "I installed Arrigo Local but it won't work!

Verify following steps:

- EXO2019 Edition 2 is installed.
- License for above version of `EXO` is installed. 
- Arrigo Local is installed. For early bird users, this step is automatically done by RS Software. Separate E-mail is sent out.
- Project is attached.
- Project is patched according to [these](#Project-Upgrade) instructions
- EXOscada is *started*.
- Start a browser and navigate to `https://localhost/arrigo` . 

# Project Upgrade

An `EXOscada` project needs upgrade. For now, we don't yet have all templates needed in EXOdesigner to make this work.  A couple of manual steps is needed to get online and going. 

- Patch your project with [this](./arrigo_local_project_patch.zip) file. It is a zip file. Unpack , Copy and overwrite the files to the EXO project root folder. 
- In `EXO designer`, open `Scada functions` and add the `Arrigo BMS` function. 
- Restart your `EXOscada`. 

## Folder classification

Each folder is possible to configure as an `ArrigoFolder` type. 

Add a file called `.foldermeta` in the EXOdesigner folder. If the file is missing, the folder type defaults to `UserArea`.

```json
{"type":"House"}
```

The value of type can be whatever you want, we refer to this later on. 

In runtime the `Shared:Arrigo/FolderTypes/.folders.json` is used to match the folder type to obtain the correct folder configuration.

If a local `folder.rwaf` exists, this file will be used .

> "I have already a dashboard configuration, what do i do?"

You must rename your `filename.rwaf` to `folder.rwaf`. Only one `.rwaf` file is allowed.
