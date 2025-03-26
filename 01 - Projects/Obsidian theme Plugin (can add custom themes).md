---
status: 🟨
tags:
  - project
links: 
deadline: 2025-02-28
area:
  - - My Areas
---


### <span style="color:red">Main Documentaries</span>

1. Plugin Page

```embed
title: "Build a plugin - Developer Documentation"
image: "https://publish-01.obsidian.md/access/caa27d6312fe5c26ebc657cc609543be/Assets/obsidian-lockup-docs.svg"
description: "Build a plugin - Developer Documentation"
url: "https://docs.obsidian.md/Plugins/Getting+started/Build+a+plugin"
```

2. Theme Page
   
```embed
title: "Themes - Obsidian Help"
image: "https://publish-01.obsidian.md/access/f786db9fac45774fa4f0d8112e232d67/Attachments/obsidian-lockup-help.svg"
description: "Themes - Obsidian Help"
url: "https://help.obsidian.md/themes"
```


---
### <span style = "color:violet">Resource</span>

```embed
title: "How to create a plugin for Obsidian"
image: "https://i.ytimg.com/vi/XaES2G3PVpg/maxresdefault.jpg"
description: "In this talk, @phibr0 will show how to create an Obsidian Plugin from start to finish. We will go over how to set everything up, how to add functionality sta…"
url: "https://youtu.be/XaES2G3PVpg?si=mz-vWZ_kP31cUT1G"
```

basics ->

```embed
title: "Let’s Build a Plugin For Obsidian October with Marcus Olsson"
image: "https://i.ytimg.com/vi/CtR-d-gyxHg/maxresdefault.jpg?sqp=-oaymwEmCIAKENAF8quKqQMa8AEB-AH-CYAC0AWKAgwIABABGEEgMCh_MA8=&rs=AOn4CLCWm7HlK2ZIwzBCKG_rA3Hf49qBjQ"
description: "Marcus walks you through how to get up and running with developing a plugin for Obsidian.Links and resources:- for Plugin Developers: https://publish.obsidia…"
url: "https://youtu.be/CtR-d-gyxHg?si=-6slJj-9AoIuUmBz"
```

Commands -> 
```embed
title: "Accept user input using commands and ribbon actions with Marcus Olsson"
image: "https://i.ytimg.com/vi/4B8imQQYM94/hqdefault.jpg?sqp=-oaymwEmCOADEOgC8quKqQMa8AEB-AH-CYAC0AWKAgwIABABGGUgZShlMA8=&rs=AOn4CLAjHHEemif6nCqtxhZCIcucsY2-dQ"
description: "Marcus walks you through accepting user input using commands and ribbon actions to make your plugin more useful.Watch this first if you haven’t: Let’s Build…"
url: "https://youtu.be/4B8imQQYM94?si=uEuOoIydc3cYj6kJ"
```

---

## <code style ="color:pink">Important</code>

[onload()](https://docs.obsidian.md/Reference/TypeScript+API/Plugin/onload) runs whenever the user starts using the plugin in Obsidian. This is where you'll configure most of the plugin's capabilities.

[onunload()](https://docs.obsidian.md/Reference/TypeScript+API/Component/onunload) runs when the plugin is disabled. Any resources that your plugin is using must be released here to avoid affecting the performance of Obsidian after your plugin has been disabled.




### <span style = "color:blue">Manifest.json</span>

```json
{  
    "id": "obsi-style",  
    "name": "ObsiStyle",  
    "version": "1.0.0",  
    "minAppVersion": "0.15.0",  
    "description": "Customize Obsidian with your own themes and matching pen colors.",  
    "author": "ZeroDark",  
    "authorUrl": "https://github.com/ZeroDark-0",  
    "fundingUrl": "https://buymeacoffee.com/zerodark",  
    "isDesktopOnly": false  
}
```

