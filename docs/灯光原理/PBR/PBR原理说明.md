# What is PBR

PBR 指的是 "Physically Based Rendering"。也就是基于物理正确的方式来计算灯光与材质，实际上这个概念很早以前就有，并且很多已知的算图引擎如 Vray、MR、甚至近几年的 Octane、Redshift 都是 Physically Based Rendering。在 Keyshot 中，高级材质也是 PBR 属性的材质。所以从理论上来说，Keyshot 也是可以渲染出非常真实的效果图的。

## 为什么 PBR 最近这么火？

> 因为 “Physically Based Rendering” 需要花费大量计算资源，游戏讲求的是即时运算，每秒 30～60 fps，不可能像是 CG 那样一张算个一小时以上，所以即便以前就有即时算图非常厉害的技术，也没有办法应用在游戏上。
>
> 以前的游戏，大多只有即时反光（Specular）随着硬件越来越强大，加上演算法的改良，这几年开始加入即时反射（Reflection）使得游戏的画面效果变得更加真实，因为是 Realtime 就可以计算出很棒的效果，而不像 CG 那样一张要算很久，所以 PBR 这三个字又突然开始热门了起来。


![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-020901.png)

在游戏界，It’s Next Generation

## We are talking about PBS

> 实际上这里的 PBR 应该称 Physically Based Shading，
> 只讨论材质在真实物理环境下的反应，
> 不讨论 AO、GI，Shadow 这些灯光和其他的部份。

Simply using a PBR shader does not make your artwork physically accurate. A PBR system is a combination of physically accurate lighting, shading, and properly calibrated art content.

> PBR 在材质上有几个重点：
> 1.材质分为导体与电介质（Conductors/dielectrics）。
> 2.所有的材质都有 Specular/Reflection 和 Glossiness/Roughness 。
> 3.贴图走线性流程。
> 4 PBR 遵守能量守恒

## Conductors And dielectrics 金属与非金属(导体与电介质/非导体)

> 这是 PBR 最重要的部份，所有的材质都会反射，
> 通常电介质的 Specular Color 会是灰阶，
> 而导体的 Specular Color 则会带有颜色。

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-020903.png)

> 视觉上来看，导体都有较强的反射，
> 大多数的电介质只要经过抛光处理就可以产生更强的反射（Specular），
> 除了 Specular Color 上的差异，电介质的 Fresnel 也较低。

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-020905.png)

> 因此我们大致上可以用 Fresnel/ior 来定义材质是导体或电介质，
> 不过切记这只是个替代方案，
> metalness/metalic 跟 Fresnel/ior 在物理上仍然是不同意义的。

如果材质经过电镀或上漆后，材质的属性会是最外层的属性。

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-020906.png)

### Albedo/Diffuse/BaseColor

> 其实都是一样东西，只是不同领域的讲法，
> 这张图代表材质本身的颜色，
> 需要去除光线、阴影、包括 AO 等等和灯光有关的资讯。
>
> ![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-020908.png)
>
> 深入点来说，
> Albedo 在非导体的时候会和 Diffuse 相同
> 在导体上会是黑色，
> 在半导体的时候，Albedo 会比 Diffuse 暗，
> 这是根据能量守恒，部份能量弹射不被材质吸收。

不过 Albedo 其实是反照率，是描述大范围面积，例如一片陆地、海洋，甚至星球等，在接受太阳辐射后的反射与吸收平均比例值，完全吸收为 0，完美反射为 1。

也就是说，Albedo 只能显示出灰阶，无法带有颜色资讯，
必须再搭配光谱（spectrum）才能组合出我们一般认知的颜色。

在 PBR 使用 Albedo 这个字其实算是误用，
但一方面也是为了和旧的游戏制作流程做区隔，
因为旧的流程 diffuse map 会带有反光和阴影。

### Specular/Metallic/Reflection

> 如同 Albedo，这三个其实也是在描述反射现象。
> 但描述的状况不同，所以得到的意思也不太一样，
> Specular 一般理解是反射上对光源的镜面反射，
> 而反射分为 Specular reflection 和 Diffuse reflection，
> 差异在于反射的模糊程度，
> Metallic 则定义材质属于金属或是非金属，

所有的材质都有反射，只是反射率上的不同。
![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-020909.png)

所以 –
Specular 其实就是没有模糊的反射，
Diffuse reflection 就是被 Glossiness 的 Specular，
Metallic 是物理性质，材质越趋近金属，反射率越强。

但是如同前面说过，
非金属的 Reflection 会是白色，金属则会带有颜色，
所以当你用 Metallic 的方式来定义反射的时候，
diffuse 和 reflection 会被改变颜色，
这是物理正确的。

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-020911.png)

### Roughnes/Glossiness

用来描述材质表面的粗糙程度，越粗糙的会产生越模糊的反射。

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-020912.png)

物理性上，材质的反射强度是根据材质表面的光滑程度与 Fresnel，
反射的颜色会根据物质的导电性改变。

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-020914.png)

### That’s all

**实际上 PBR 只使用三张贴图 albedo、metalness、roughness**
它简化了材质的作法，并且得到接近物理正确的效果，
重点是有了反射，一切都变得真实许多。
![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-020915.png)
其他如 normal 之类的 Map，那是上个世代的技术了。

## 所以到底怎么用在 Vray 上？

> 大部分的状况下，PBR 的贴图可以直接使用在 Vray 之类的算图引擎。

Fresnel, in Toolbag 2 and most PBR systems, is approximated automatically by the BRDF, in this case Blinn-Phong or GGX, and usually does not need an additional input. However, there is an extra control for Fresnel for the Blinn-Phong BRDF, which is meant for legacy use as it can result in non physically accurate results.

> ![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-020917.png)

> Matelic 0~1
> ![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-020918.png)
> ![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-020920.png)
>
> Colored
> ![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-020921.png)
> ![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-020924.png)

> Roughness 0~1
> ![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-020925.jpg)
> ![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-020927.png)

> Shader Material
> ![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-020929.png)
> ![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-020932.png)

> 毕竟是不同的解算引擎，所以你只能得到很近似的效果，
> 颜色和数值强度上还是会有些落差，
> 而且一开始就有提到，Matelic 和 Fresnel 本来就不相同，
> 只是我们这里用 Matelic 数值代替 Fresnel 得到近似值。

这有点类似用单眼拍照时，你会有光圈先决，快门先决，也会有 M 模式。

PBR 提供了 Matelic 先决模式，
你调整 Matelic，其他 diffuse color、reflection color、fresnel 等等都会自动调整，
使用者可以很轻易的调出好看的材质。

Vray 材质提供的是 M 模式，你所有的数值都要自己调整，
可以更精准的调出各种想要的材质，但是也可能调出很奇怪的结果。

> 此外，虽然 PBR（PBS）声称是能量守恒，
> 但实际上它忽略了灯光与阴影，以及 diffuse 散发的能量等等细节，
> 而这些在 CG 用的算图引擎都会加入计算，
> 因此无法得到完全一样的结果。

> Simply using a PBR shader does not make your artwork physically accurate. A PBR system is a combination of physically accurate lighting, shading, and properly calibrated art content.

> 此外，以目前游戏用的 PBR 规范，
> 是有舍弃掉一部分的 Fresnel 范围，
> 最小值大约是 1.5～1.6 之间，
> 低于 1.4 的材质，用 PBR 是模拟不出来的。

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-020935.jpg)

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-020905.png)

> 另外，其实很多材质没有办法单纯的用导体或非导体决定反射是否带有颜色，
> 例如半透明的物体，或是混合材质。
>
> ![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-020944.png)

------

## 后记

> 其实以 “Physically Based Rendering” 来说，
> 我们需要做的不是导入什么软件，
> 或是用几张贴图来控制材质，
> 而是如果我们要把 CG 做的写实，
> 那么我们就应该用有根据的方式来制作材质，
> 而不是依赖直觉或是经验来调整参数。
>
> 如果你今天要做塑胶材质，
> 但是却为了效果把反射加上颜色或全白，
> 或是为了要反射强一点把 IOR 调很高，
> 这些都会产生非真实的材质，
> 即使看起来好看。
>
> 如果你要做的是一个金属材质，
> 那 Reflection 和 Diffuse 的颜色应该要做相对应的处理，
> 而不是单纯只有把 ior 调高，
> 也不要怀疑 Reflection Pass 可能会带有颜色。

# 也许错误的是使用者，而不是算图引擎。

### 参考文献

- [Physically Based Rendering for Artists by -Andrew Maximov](http://artisaverb.info/PBR.html)
- [Feeding a physically based shading model](https://seblagarde.wordpress.com/2011/08/17/feeding-a-physical-based-lighting-mode/)
- [Defining PBR (Physically-Based Rendering) Graphics with Crytek Developers](http://www.gamersnexus.net/gg/1866-what-is-pbr-cryengine-star-citizen)
- [IorInfo](http://refractiveindex.info/)
- [Albedo vs Diffuse](http://computergraphics.stackexchange.com/questions/350/albedo-vs-diffuse)
- [diffuse, baseColor, albedo??](https://forum.allegorithmic.com/index.php?topic=4177.0)
- [Physically Based Rendering from Toolbag](http://www.marmoset.co/toolbag/learn/pbr-practice)
- [Monsters University: rendering physically based monsters](https://www.fxguide.com/featured/monsters-university-rendering-physically-based-monsters/)
- [PHYSICALLY BASED RENDERING in 3Dcoat](http://3dcoat.com/pbr/)
- [Why doesn’t dielectric materials have coloured reflections like conductors?](http://physics.stackexchange.com/questions/213478/why-doesnt-dielectric-materials-have-coloured-reflections-like-conductors)
- [Brief Considerations About Materials](http://www.manufato.com/?p=902)
