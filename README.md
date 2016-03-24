   最近做一个项目，因为是上一个项目的升级版本，就沿用了上个项目的导航栏用的是a标签跳转，刷新整个页面来实现，刚开始都还比较顺利，但是后来跟后台对接的时候，我们后台用的是java，所以需要把前台页面改成JSP，而且通过Sitemesh把left部分的导航栏以及top的banner部分，还有footer部分独立出来。
   原本我是通过在每个页面中都单独写一套导航栏的代码（虽然有点麻烦）来实现，我们导航栏是二级的菜单，当实现点击链接跳转刷新页面的时候，必须要让这个链接在新页面的父级元素展开（open），我的实现方式是在每个页面中，给所在链接的父级元素添加class="open"，这样当进入新的页面的时候，这个元素就是展开的。但是随着把导航栏独立出来，问题就来了，之前靠着class="open"的方法已经不能使用。
   这时我想到的解决办法是通过，给所有的a元素，display=“none”的属性，然后当跳转到新页面的时候，通过location.href.indexOf（）和location.href.substr()，提取出某个字符段，然后利用each方法遍历所有的a元素，通过判断a元素是否包含提取出来的字符段，如果满足条件的话，就找到祖先级元素，添加class=“open”，同事给父级元素添加display=“block”，让元素显现出来。
   因为是公司内部系统，所以只要考虑公司电脑的型号就可以了，当然是上媒体查询，通过
   @media (min-width:1200px){.container{width:1349px}}
   @media (min-width:1400px){.container{width:1383px}}
   @media (min-width:1600px){.container{width:1583px}}
   @media (min-width:1750px){.container{width:1733px}}
   @media (min-width:1900px){.container{width:1903px}}
   不过我是直接修改了bootstrap的源码，还有container的padding-left,padding-right默认的是15px,我也给改成了0；
