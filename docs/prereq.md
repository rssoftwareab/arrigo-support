---
layout: main
title: Installation.
description: instructions and binaries
---
# How Do I start?

`Arrigo Local` needs `EXO2019 Edition 3` to run. 

> "I installed Arrigo Local but it won't work!

Verify following steps:

- EXO2019 Edition 3 is installed.
- License for `EXOscada 2019` is installed. 
- Arrigo Local is installed.
- Project is attached.
- Project is updated according to [these](#Project-Upgrade) instructions
- The "Arrigo BMS" Scada Function is added to the Main Computer
- EXOscada is *started*.
- Start a browser and navigate to `https://localhost/arrigo` . 

# Project Upgrade

An `EXOscada` project needs upgrade. A couple of manual steps are needed to get online and going. 

- In `Project Builder`, add the object `Arrigo BMS` from the `General objects` category. This will copy necessary files to the project and give access to the new tools.
- In `Project Builder`, select the `Main Computer` and open `Scada functions` - add the `Arrigo BMS` function. 
- Restart your `EXOscada`. 
