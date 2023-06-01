---
title: Hexo的Next主题自定义样式
date: 2023-03-23
tags: hexo
description: 
---

# 自定义主题样式

## &#x1F308;添加动态背景

> <font color="#f60"><b>注意</b></font> ：如果 next 主题在 5.1.1 以上的话就不用我这样设置，直接在主题配置文件中找到 canvas_nest: false，把它改为 canvas_nest: true 就行了（注意分号后面要加一个空格）
<!-- more -->

### 修改 <span style="color:#f60;background-color:#f0f0f0;border:1px solid #D9D9D9;padding:3px;font-weight:700">\_layout.swig</span>

<p><span>打开 </span><span style="color:#f60;background-color:#f0f0f0;border:1px solid #D9D9D9;padding:3px;font-weight:700">themes / next / layout / _layout.swig</span></p>

 <p>在 <span style="color:#f60;background-color:#f0f0f0;border:1px solid #D9D9D9;padding:3px;font-weight:700">< /body></span> 之前添加代码(注意不要放在< /head>的后面)</p>
  
```
{% if theme.canvas_nest %}
<script type="text/javascript" src="//cdn.bootcss.com/canvas-nest.js/1.0.0/canvas-nest.min.js"></script>
{% endif %}
```

### 修改配置文件

<p><span>打开 </span><span style="color:#f60;background-color:#f0f0f0;border:1px solid #D9D9D9;padding:3px;font-weight:700">themes / next / _config.yml</span><span>，在里面添加如下代码：(可以放在最后面)</span></p>

```
# --------------------------------------------------------------
# background settings
# --------------------------------------------------------------
# add canvas-nest effect
# see detail from https://github.com/hustcc/canvas-nest.js
canvas_nest: true
```

到此就结束了，运行 hexo clean，然后运行 hexo g,然后运行 hexo s

如果感觉默认的线条太多的话，可以改为

```
{% if theme.canvas_nest %}
<script type="text/javascript"
color="0,0,255" opacity='0.7' zIndex="-2" count="99" src="//cdn.bootcss.com/canvas-nest.js/1.0.0/canvas-nest.min.js"></script>
{% endif %}
```

#### 配置项说明

- color ：线条颜色, 默认: '0,0,0'；三个数字分别为(R,G,B)
- opacity: 线条透明度（0~1）, 默认: 0.5
- count: 线条的总数量, 默认: 150
- zIndex: 背景的 z-index 属性，css 属性用于控制所在层的位置, 默认: -1

