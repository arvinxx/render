KeyShot中Poliigon贴图的使用方法整理
===================================

Poliigon是国外著名的优质贴图资源站。

\> Their wide array of high quality textures are rich in detail, can be used
across different 3D software and come with various map types to get your models
looking much more realistic than they would otherwise.

那在Keyshot中如何去使用这些优质的贴图呢？下面就开始介绍这些高质量贴图的使用方法。

1.  将Keyshot的材质设置成高级材质

只有高级材质才拥有使用这些贴图的必要通道，并且高级材质保持能量守恒。

![](http://ox55f9bg6.bkt.clouddn.com/2017-10-04-054609.jpg)

1.  将贴图贴到对应的贴图通道中。

KeyShot贴图通道和 Poliigon贴图类型的对应关系如下：

KeyShot通道 \| Poliigon贴图

Diffuse → Color

Specular → Reflection

Bump → Normal

Roughness → Gloss

1.  调整贴图的参数设置

贴图的个别参数会根据实际模型进行调整，例如UV贴图模式、法线方向、贴图缩放尺寸等。

此外，Poliigon的Gloss贴图需要进行反转处理，因为roughness（粗糙度）和gloss（光泽度）正好是完全相反的两个参数。用公式来说明的话就是：

roughness = 1 - gloss

normal贴图在连接进bump通道之后，需要勾上normal参数

![](http://ox55f9bg6.bkt.clouddn.com/2017-10-04-054612.jpg)

1.  增加表面破损纹理

真实世界的物体必然存在不完美特征，例如划痕、指纹、磨损等。如果我们要让一个材质看着无比逼真，那么我们应该给它加上一些缺陷的特征。

具体操作就是新建一个diffuse材质，连接到label通道，然后加一张缺陷贴图到这个diffuse材质的不透明通道上，稍作调整即可表达出逼真的效果。

![](http://ox55f9bg6.bkt.clouddn.com/2017-10-04-054611.jpg)

最终的效果图：

![](http://ox55f9bg6.bkt.clouddn.com/2017-10-04-054614.jpg)

![](http://ox55f9bg6.bkt.clouddn.com/2017-10-04-054617.jpg)

参考资料
--------

How to Use Poliigon Textures in KeyShot:
<https://blog.keyshot.com/how-to-use-poliigon-textures-in-keyshot>

Using Poliigon textures in KeyShot - Part 1 (Material Basics):
<https://m.youtube.com/watch?v=_yj9zQ_oacY#action=share>

Using Poliigon textures in KeyShot - Part 2 (Surface Imperfection Overlays):
<https://m.youtube.com/watch?v=BetK06dMi-E>
