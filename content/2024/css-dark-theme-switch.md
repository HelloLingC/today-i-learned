---
title: 'CSS 黑暗/日间主题切换'
date: 2024-08-11T04:51:37+08:00
draft: false
categories:
tags: [css]
---

使用媒体查询prefers-color-scheme

```
@media (prefers-color-scheme: {mode}) {

}
```


```
:root {
  --color: #333;
  --bg-color: #eee;
}

@media (prefers-color-scheme: dark) {
  :root {
    --color: #ccc;
    --bg-color: #1f1f1f;
  }
}
```

如果要判断当前的主题，可以用：

```
const mediaQueryListDark = window.matchMedia('(prefers-color-scheme: dark)');
if (mediaQueryListDark.matches) {
  // 系统当前是暗色(dark)主题
}

const mediaQueryListLight = window.matchMedia('(prefers-color-scheme: light)');
if (mediaQueryListLight.matches) {
  // 系统当前是亮色(light)主题
}
```

有意思的是，甚至能监听系统主题的变动：

```
function handleChange (mediaQueryListEvent) {
  if (mediaQueryListEvent.matches) {
    // 用户切换到了暗色(dark)主题
  } else {
    // 用户切换到了亮色(light)主题
  }
}

const mediaQueryListDark = window.matchMedia('(prefers-color-scheme: dark)');

// 添加主题变动监控事件
mediaQueryListDark.addListener(handleChange);

// 移除主题变动监控事件
mediaQueryListDark.removeListener(handleChange);
```

# 切换主题按钮

如果要手动切换主题，最常用的就是改变根元素的classname。
