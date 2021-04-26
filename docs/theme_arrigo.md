---
layout: main
title: Theming
description: It's all about style
---
# Theme settings in Arrigo

> NOTE: Theme changes are overwritten during installation of Arrigo Local!
>
> The Theme folder needs to be copied into the product after upgrade. We know this and have a plan. 

All theme settings resides in the theme file, in frontend folder. Prepare with the following steps:

- In Arrigo Local the theme folder should be overridden in `Program Files\Arrigo\Arrigo Local\Frontend\theme`. Create that folder.

- Copy the theme files [here](./theme_arrigo/index.md) and put them in the newly created folder above.  

You can now override the theme settings.

> Remember to back up your theme settings, including the images in the image folder. Easiest way is to create a backupfolder with two folders inside, one for images, and one for theme folder. 

## Arrigo BMS legazy theme from EXOscada.

We now support legacy theming in views!

By inserting //LegacyTheme as the first row in the OnOpen-attribute of the View in ViewDesigner, Arrigo theming will be ignored when opening the view, letting font families and sizes be determined from the Shared/theme/Standard.cwvt.json-file instead.

## Change pictures on login page

Imagine you want to change the splash images. The big image at the right on desktop is called `splash` and the small waves below login form is called `small_splash`. 

Put your new `mySplash.png` and `mySmallSplash.png` in  `images` folder.

Change `theme.json ` in `theme` folder:

```
  "login": {
    "images": {
      "splash": "mySplash.png",
      "small_splash": "mySmallSplash.png",
      "show_small_splash_on_desktop": false
    }
```

If you want to show the small splash on desktop and big screens, set `show_small_splash_on_desktop` to `true`.

Save the file. Reload Arrigo with `Ctrl+F5` to fetch the new theme settings. 

## Change logo in header

Put your new `myLogo.png` in `images` folder. 

If you need to adjust the height of the header, simply increase the numbers in the `height` section of the `theme.json`. `small`  is mobile settings, and `normal` is desktop.

Change `theme.json` in `theme` folder to set the new logo:

```
 "header": {
    "images": {
      "logo": "myLogo.png"
    },
    "height": {
      "normal": "70px",
      "small": "55px"
    }
  },
```

## Change theme colors

Edit the `colors.light.json` and `colors.dark.json` to match your logo and visual style of your project. 
