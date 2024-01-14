---
title: "God mode in a browser"
seoDescription: "Unlock God Mode: Edit any website text instantly with this browser console trick or bookmarklet. Transform your browsing experience!"
datePublished: Sun Jan 14 2024 04:27:56 GMT+0000 (Coordinated Universal Time)
cuid: clrczwqcb000209l75b78cco3
slug: god-mode-in-a-browser
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1705206391064/ba80765f-9ecb-417c-aa36-40dc2c8fbb6b.png
tags: browser, tricks, javascript, tools, god, god-mode

---

With the help of god mode, you can modify any text on a website. Yes, **any text**.

![God mode explained](https://cdn.hashnode.com/res/hashnode/image/upload/v1705206226752/fcbee2dc-9b86-4ee3-a210-141109189e0e.gif align="center")

```javascript
document.designMode = "on"
```

Write the above in your browser console or

```javascript
javascript:((d,o,m)=>{d[m]=d[m]!==o?o:"off"})(document,"on","designMode");
```

Make a bookmark with the above as the URL.