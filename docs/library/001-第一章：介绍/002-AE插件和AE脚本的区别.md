## AE插件和AE脚本的区别
 &#160;&#160;&#160;&#160;&#160;&#160;（1）从功能实现来看：AE几乎可以操作AE所有内部对象，对于不同的对象，分别有不同的插件类型，如渲染输出和素材导入都由AEIO插件控制、AE里面各种酷炫的特效都由特效插件实现、还有各种图层、关键帧则通过AEGP插件来定制等等；而AE脚本只有这么一种，它有两种调用方式，可以使用Script Panel文件夹和直接通过文件菜单项的执行某脚本来实现，或者通过ESTK来动态连接来实现，它可以操作的对象比之AE插件少了许多，可以说，AE脚本做到的，AE插件都可以做到，而且执行效率更高，不过AE脚本有一个无以伦比的优点，开发效率相当高，不必像插件开发那样需要搭建相应的开发环境，只需要找到一个文本编辑器就能够开发啦，而且官方也提供了ESTK这样的包含智能代码提示的强大文本编辑器来实现编写AE脚本，就目前脚本的定位而言，它比较适合用来编写一些自动化的操作，比如批量处理文字特效，将某类特效的功能封装成脚本，方便以后一键生成等等，目前最强大的脚本应该就是愤怒的小鸟的动画版里用到的AE脚本了，非常强大，另外还有各种MG动画的神器Motion Toolkit等等。ㄟ(≧◇≦)ㄏ
<br>
 &#160;&#160;&#160;&#160;&#160;&#160;（2）从开发方式来看：插件使用静态语言编写，如windows下使用C/C++来实现，而在Mac下则使用Object-C来实现；而脚本则统一使用 *Adobe ExtendScript* 来实现的。(。＾▽＾)

***
> 注意：
*Adobe ExtendScript* 是基于 *EMCA标准*，为Adobe产品专门定制过的JavaScript，注意，这个被Adobe定制后的JavaScript和Web里的JavaScript还是有相当大的区别滴，不过不用纠结它们之间的语法差异，因为它们是一样的。(￣︶￣)↗

***
### *没图你说个JB[no pictue no talk]：*
<div  align="center">    
<img src="assets/001/001-a16c319b.png" width = "800" alt="AE插件和AE脚本的放置目录区别" align=center />
</div>
<div  align="center">    
<img src="assets/001/001-e0835ce2.png" width = "800" alt="AE插件和AE脚本的调用区别" align=center />
</div>
<div  align="center">    
<img src="assets/001/001-a75a7363.png" width = "800" alt="开发者编写AE插件和AE脚本的工具区别" align=center />
</div>
