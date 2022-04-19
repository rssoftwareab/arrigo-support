---
layout: main
title: Theming
description: It's all about style
---
# Theme settings in Arrigo

> NOTE: There is an issue with old theme files (prior to 16 March, 2022), read more [here](https://github.com/rssoftwareab/arrigo-support/blob/master/docs/support/index.md#adding-new-chart-signal-gives-this-content-was-not-properly-loaded).

All theme settings resides in the theme file, in frontend folder. Prepare with the following steps:

- In Arrigo Local the theme folder should be overridden in `Program Files\Arrigo\Arrigo Local\Frontend\theme`. Create that folder.

- Copy the theme files [here](./theme_arrigo/index.md) and put them in the newly created folder above.  

You can now override the theme settings.

> Remember to back up your theme settings, including the images in the image folder. Easiest way is to create a backupfolder with two folders inside, one for images, and one for theme folder. 

## Arrigo BMS legacy theme from EXOscada.

We now support legacy theming in views!

By inserting //LegacyTheme as the first row in the OnOpen-attribute of the View in ViewDesigner, Arrigo theming will be ignored when opening the view, letting font families and sizes be determined from the Shared/theme/Standard.cwvt.json-file instead.

## Change pictures on login page

Imagine you want to change the images on the login page. You can add or modify the left large image, the top centered images and an image at the bottom right.

Make sure your images are located in the "images" folder (`Program Files\Arrigo\Arrigo Local\Frontend\images`). Normal graphics formats are supported such as jpg, png, svg.

Change `theme.json ` in `theme` folder as follows:

```
  "login": {
    "layout": {
      "name": "splash",
      "left_splash_image": "/arrigo/images/my_new_left_splash_image.png",
      "top_center_image": "/arrigo/images/a_logo_or_something_else.png",
      "bottom_right_image": "/arrigo/images/yet_another_logo_or_image.png"
```
Make sure the name field is set to "splash" and that the path to the images are included.

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

## Additonal properties theme.json

A couple of additional custom styling implementations has been made into Arrigo.  

| Property | Value | Description |
| -------- | ----- | ----------- |
| `forcePanelMode` | `Yes` |  This will prevent the user from using the original navigation in Arrigo, enforcing the use of the Panel mode navigation at the top of the page. |
|`hidePanelModeDivider` | `Yes` | This will hide the divider line between the top header and the navigation part of the panel mode in Arrigo. |
| `minimizeContainerPaddingForViewsOnMobile` | `Yes` | This will allow the Animation views from ExoScada to be rendered without any side padding at all in Arrigo, freeing up a couple of pixels of width. |
| `includeAnimationViewsInTheme` | `Yes` | This will change the theme used in Animation views to be fetched from S00004001 instead of S00004000 |
| `maintenanceText` | `Empty string` | This setting overrides current, translated, maintenance text to a custom string. |