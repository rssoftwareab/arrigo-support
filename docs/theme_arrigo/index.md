---
layout: main
title: Themes
description: Put this in your theme folder
---

# Theme files

`theme.json`

```json
{
  "page_title": "",
  "header": {
    "images": {
      "logo": ""
    },
    "height": {
      "normal": "70px",
      "small": "55px"
    },
    "logo_height": {
      "normal": "24px",
      "small": "15px"
    },
    "link_icons_height": ""
  },
  "login": {
    "layout": {
      "name": "",
      "left_splash_image": "",
      "top_center_image": "",
      "bottom_right_image": ""
    },
    "images": {
      "main_top_right_splash": "",
      "main_bottom_left_splash": "",
      "left_bottom_splash": "",
      "mobile_splash": "",
      "logo": ""
    }
  },
  "general": {
    "gutter": {
      "large": "58px",
      "medium": "34px",
      "normal": "25px",
      "small": "16px",
      "xsmall": "8px"
    },
    "desktop_width": "1200px",
    "phone_width": "667.5px"
  },
  "buttons": {
    "height": "40px",
    "min_width": "65px",
    "icon": {
      "width": "14px",
      "height": "14px"
    },
    "ripple": true
  },
  "widgets": {
    "height": {
      "normal": "321px",
      "small": "264px"
    },
    "width": {
      "normal": "565px",
      "small": "272px"
    }
  },
  "sidebar": {
    "width": "350px"
  },
  "icons": {
    "icon_width": "20px",
    "icon_size": "12px",
    "icon_line_height": 1
  },
  "fonts": {
    "family": "Proxima Soft",
    "sizes": {
      "xxxl": "32px",
      "xxl": "28px",
      "xl": "24px",
      "lg": "18px",
      "md": "16px",
      "sm": "14px",
      "xs": "13px",
      "xxs": "12px",
      "xxxs": "11px",
      "xxxxs": "10px",
      "xxxxxs": "9px"
    },
    "weights": {
      "regular": 300,
      "medium": 500,
      "semibold": 700,
      "bold": 900
    }
  },
  "borders": {
    "style": "solid",
    "enabled": true,
    "radius": {
      "size": "5px",
      "enabled": true
    },
    "sizes": {
      "default": "1px"
    }
  },
  "inputs": {
    "floatinglabel": false,
    "outline": {
      "enabled": false
    },
    "width": {
      "full": "100%",
      "lg": "400px",
      "md": "300px",
      "sm": "250px",
      "xs": "200px"
    },
    "height": "40px"
  },
  "offlineBanner": {
    "height": {
      "md": "40px",
      "lg": "72px"
    }
  },
  "helpers": {}
}



```

`colors.light.json`

```json
{
  "backgrounds": {
    "colors": {
      "primary": "#FFFFFF",
      "alt": "#F7F8F9",
      "login": "#FFFFFF",
      "gradient": {
        "from": "#191c33",
        "to": "#242848"
      }
    }
  },
  "colors": {
    "order": [
      "primary.default",
      "primary.info",
      "primary.additional_1",
      "primary.additional_2",
      "primary.additional_3",
      "primary.additional_4",
      "primary.additional_5",
      "primary.additional_6"
    ],
    "primary": {
      "default": "#328BFF",
      "title": "#1A1D35",
      "text": "#1A1D35",
      "okay": "#06C8A1",
      "info": "#A55FFF",
      "warn": "#FFAE50",
      "error": "#FF4C62",
      "additional_1": "#43D8FF",
      "additional_2": "#FF6AE2",
      "additional_3": "#FDD52C",
      "additional_4": "#BDCEBE",
      "additional_5": "#B9936C",
      "additional_6": "#C94C4C",
      "login_label": "#85919D",
      "login_label_mobile": "#FFF"
    },
    "alt": {
      "default": "#286ECA",
      "okay": "#1CA388",
      "info": "#834BCB",
      "warn": "#D7821E",
      "error": "#DE5162"
    },
    "opacity": 0.2
  },
  "grayscale": {
    "primary": {
      "default": "#1A1D35",
      "accent": "#FFFFFF",
      "neutral": "#85919D"
    },
    "alt": {
      "default": "#78AEFF",
      "accent": "#FFFFFF",
      "neutral": "#1A1D35"
    },
    "opacity": 0.2
  },
  "legacy": {
    "primary": {
      "red": "#800000",
      "lightRed": "#FF0000",
      "green": "#008000",
      "lightGreen": "#00FF00",
      "darkAqua": "#209090",
      "blue": "#000080",
      "lightBlue": "#0000FF",
      "cyan": "#008080",
      "lightCyan": "#00FFFF",
      "magenta": "#800080",
      "lightMagenta": "#FF00FF",
      "brown": "#808000",
      "olive": "#808040",
      "yellow": "#FFFF00",
      "black": "#000000",
      "darkGray": "#606060",
      "gray": "#808080",
      "lightGray": "#C0C0C0",
      "white": "#FFFFFF",
      "paleDarkRed": "#C04040",
      "paleRed": "#FF8080",
      "palePink": "#FFA0C0",
      "paleOrange": "#FFC040",
      "paleDarkPink": "#C000C0",
      "paleDarkOrange": "#FF6020",
      "paleBrown": "#C08020",
      "paleYellow": "#FFFF80",
      "paleDarkBlue": "#4040C0",
      "paleBlue": "#8080FF",
      "paleLightBlue": "#C0FFFF",
      "palePurple": "#C0A0FF",
      "paleDarkPurple": "#8040C0",
      "paleGreen": "#80C080",
      "paleDarkGreen": "#408040"
    }
  },
  "borders": {
    "color": "#E9EDF1"
  },
  "shadows": {
    "color": "#85919D",
    "opacity": 0.18
  },
  "inputs": {
    "backgrounds": {
      "normal": "#FFFFFF",
      "disabled": "#F7F8F9"
    },
    "border": {
      "color": "#bec5cb"
    }
  },
  "buttons": {
    "icon": {
      "color": "#FFFFFF"
    }
  }
}


```

`colors.dark.json`

```json
{
  "backgrounds": {
    "colors": {
      "primary": "#2b2f37",
      "alt": "#1f2128",
      "login": "#85919D",
      "gradient": {
        "from": "#090c1b",
        "to": "#2b2f37"
      }
    }
  },
  "colors": {
    "order": [
      "primary.default",
      "primary.info",
      "primary.additional_1",
      "primary.additional_2",
      "primary.additional_3",
      "primary.additional_4",
      "primary.additional_5",
      "primary.additional_6"
    ],
    "primary": {
      "default": "#328BFF",
      "title": "#eaeaeb",
      "text": "#eaeaeb",
      "okay": "#06C8A1",
      "info": "#ca63ff",
      "warn": "#FFAE50",
      "error": "#FF4C62",
      "additional_1": "#43D8FF",
      "additional_2": "#FFAAFF",
      "additional_3": "#FDD52C",
      "additional_4": "#BDCEBE",
      "additional_5": "#B9936C",
      "additional_6": "#C94C4C",
      "login_label": "#eaeaeb",
      "login_label_mobile": "#FFF"
    },
    "alt": {
      "default": "#286ECA",
      "okay": "#1CA388",
      "info": "#834BCB",
      "warn": "#D7821E",
      "error": "#DE5162"
    },
    "opacity": 0.2
  },
  "grayscale": {
    "primary": {
      "default": "#eaeaeb",
      "accent": "#ffffff",
      "neutral": "#85919D"
    },
    "alt": {
      "default": "#78AEFF",
      "accent": "#c6c7c8",
      "neutral": "#1A1D35"
    },
    "opacity": 0.2
  },
  "legacy": {
    "primary": {
      "red": "#800000",
      "lightRed": "#FF0000",
      "green": "#008000",
      "lightGreen": "#00FF00",
      "darkAqua": "#209090",
      "blue": "#000080",
      "lightBlue": "#0000FF",
      "cyan": "#008080",
      "lightCyan": "#00FFFF",
      "magenta": "#800080",
      "lightMagenta": "#FF00FF",
      "brown": "#808000",
      "olive": "#808040",
      "yellow": "#FFFF00",
      "black": "#000000",
      "darkGray": "#606060",
      "gray": "#808080",
      "lightGray": "#C0C0C0",
      "white": "#FFFFFF",
      "paleDarkRed": "#C04040",
      "paleRed": "#FF8080",
      "palePink": "#FFA0C0",
      "paleOrange": "#FFC040",
      "paleDarkPink": "#C000C0",
      "paleDarkOrange": "#FF6020",
      "paleBrown": "#C08020",
      "paleYellow": "#FFFF80",
      "paleDarkBlue": "#4040C0",
      "paleBlue": "#8080FF",
      "paleLightBlue": "#C0FFFF",
      "palePurple": "#C0A0FF",
      "paleDarkPurple": "#8040C0",
      "paleGreen": "#80C080",
      "paleDarkGreen": "#408040"
    }
  },
  "borders": {
    "color": "#3d404a"
  },
  "shadows": {
    "color": "#000",
    "opacity": 0.6
  },
  "inputs": {
    "backgrounds": {
      "normal": "#282a31",
      "disabled": "#30343c"
    },
    "border": {
      "color": "#595d6b"
    }
  },
  "buttons": {
    "icon": {
      "color": "#FFFFFF"
    }
  }
}

```

