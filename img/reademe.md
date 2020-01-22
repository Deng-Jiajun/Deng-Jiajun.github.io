

1. hugo的静态文件放置在/static 文件夹下

2. hugo生成的public文件夹（即整个网页静态文件），会将static里的内容放到网站根目录

3. 基于以上两点，图片的相对路径要写成这种格式：`![imagename](/img/imagename.png)`

4. 由于markdown和生成的html的图片路径是一致的，因此markdown里也要这么写。但是如果直接把图片放到 /static/img里，在本地就无法正常显示这个文件夹。

   > 显然不能，因为路径不一致：
   >
   > static：C:\Users\Deng-\OneDrive\HugoBlog\static\img
   >
   > markdown：C:\Users\Deng-\OneDrive\HugoBlog\content\post

基于以上4点原因，解决方案有以下几种：

1. 在/img里放图片，然后复制到\static\img；

   评价：麻烦

2. 在1的基础上，写一个批处理，完成复制的任务；（因为之前写过的批处理：生成public.cmd，只要在前面加上复制的命令就行）;

   评价：可行，但是不完美，可能出现文件权限问题

3. 不管，就当瞎了，本地不看，直接看server实时渲染；

   评价：可行，但是太惨了

4. 做一个link，链接两个文件夹

   评价：一劳永逸，可行。

命令如下：

`mklink C:\Users\Deng-\OneDrive\HugoBlog\content\img C:\Users\Deng-\OneDrive\HugoBlog\static\img /J`