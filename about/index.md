# 关于-About

<!--more-->
<!-- {{< typeit >}}
<center>
<span  style='font-family: MMT,"沐目体";font-size:20px;font-weight:bold;color:#009966;' >
莫笑少年江湖梦，谁不少年梦江湖。曾经年少立志三千里，如今踌躇百步无寸功。

懵懂半生，庸碌尘世中，转眼高堂皆白发，儿女蹒跚学堂中。碎银几两催人老。

心仍少，皱纹却上眉目中，浮生醉酒回梦里。青春人依旧，只叹时光太匆匆！
</span>
</center>
{{< /typeit >}} -->

<!-- A root element for TypeIt to target. -->
<center>
<span id="typeitObj" style='font-family: MMT,"沐目体";font-size:20px;font-weight:bold;color:#009966;' >
莫笑少年江湖梦，谁不少年梦江湖。曾经年少立志三千里，如今踌躇百步无寸功。
<br/>懵懂半生，庸碌尘世中，转眼高堂皆白发，儿女蹒跚学堂中。碎银几两催人老。
<br/>心仍少，皱纹却上眉目中，浮生醉酒回梦里。青春人依旧，只叹时光太匆匆！
</span>
</center>
<!-- The script itself, loaded AFTER your root element. 
https://www.typeitjs.com/docs/vanilla/usage#options
-->
<script src="https://unpkg.com/typeit@8.7.1/dist/index.umd.js"></script>
<script>
    new TypeIt("#typeitObj", {
      speed: 150,
      loop: true,
      loopDelay: 1000,
      cursor: true,
      cursorChar: '|',
      html: true
    }).go();
</script>


<!-- metingJs 音乐插件 -->
{{< music auto="https://y.qq.com/n/yqq/playlist/8138088068.html" fixed=false list-folded=true autoplay=true volume="0.2" order="random" loop="all"  >}}


<!-- 
> typeit 示例

```markdown
{{</* typeit */>}}
这一个带有基于 [TypeIt](https://typeitjs.com/) 的 **打字动画** 的 *段落* ...
{{</* /typeit */>}}
```

{{< music auto="https://y.qq.com/n/yqq/playlist/8138088068.html" fixed=true list-folded=false autoplay=true volume="0.2" >}} -->

<!-- {{< music url="/music/Take-Me-To-Your-Heart.mp3"  name="Take-Me-To-Your-Heart" artist="Michael Learns To Rock" cover="/logo.png" volume="0.2" autoplay=true loop=all fixed=true >}} -->

<!-- ```markdown
{{</* music url="/music/Take-Me-To-Your-Heart.mp3"  name="Take-Me-To-Your-Heart" artist="Michael Learns To Rock" cover="/logo.png" volume="0.2" autoplay=true loop=all */>}}
``` 
-->


---

> 作者: [geekswg](https://geekswg.github.io)  
> URL: https://geekswg.github.io/about/  

