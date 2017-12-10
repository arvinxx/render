# HDR Light Studio For Rhinoceros 工作流程介绍



​      HDR Light Studio是非常实用的灯光设计软件，可以和很多3维软件联合使用。HDR Light Studio的使用也是非常简单、高效。

​      HDR Light Studio 与Rhino联合使用方式。

## General Workflow

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-012427.jpg)

 

​      单击+按钮，添加一个新环境。这个【Open】窗口基于使用的渲染器会不一样。

 

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-012417.jpg)

 

​      单击【More Types…】按钮，在列表中选择HDR Light Studio，然后单击OK。

 

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-012416.jpg)

 

注：HDR Light Studio Enviroment 是 HLS 的一个 Rhino 插件  

[HDR Light Studio v5.3 Win激活版 + 插件接口 下载地址](http://www.gfxcamp.com/hdr-light-studio-v53/)

 

​      【Environments Editor】面板会出现一个激活的“HDR Light Studio Environment 001”选项，当HDR Light Studio环境是激活的，在下面可以看到HDR Light Studio链接控制，单击【Show Light Studio】按钮，启动HDR Light Studio。HDR Light Studio就会启动，环境贴图会链接到Rhino。可以将HDR Light Studio界面放置在第二个显示器上，或调整他的大小使Rhino仍可见。

 

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-012421.jpg)

 

​      在HDR Light Studio中创建一个灯光，HDRI map会与Rhino共享，每次改变都会更新。

 

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-012429.jpg)

 

​      默认HDR Light Studio的rendered view显示的是茶壶模型，但是这个视窗在使用Rhino是可以关闭的。可以直接在Rhino中决定照明效果。

 

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-012420.jpg)

 

​      要是你要保存Rhino场景，或嵌入HDR Light Studio项目，都会共享HDR Light Studio中低分辨率的HDRI map。但是要渲染更高质量，HDRI map高分辨率版本，需要单击Rhino中的HDR Light Studio控制按钮【Render】。

​      单击后，再查看HDR Light Studio软件，你会看到【Production Render】窗口，选择HDRI map的分辨率，然后单击Render按钮，高分辨率的HDRI map会生成并与Rhino共享。要是你保存Rhino项目，这个高分辨率的HDRI map也会嵌入到你的场景文件中。

 

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-012411.jpg)

 

​      如果你想渲染灯光设计到你硬盘中的HDRI map文件夹 ，以便其他用户没有HDR Light Studio也能打开Rhino项目，在Rhino中单击Bake按钮。

​      单击HDR Light Studio软件，在【Production Render】窗口中，单击【Browse】按钮选择一个文件路径，给一个文件名，再单击【Render】按钮。

 

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-012426.jpg)

 

​      现在在【environment】面板可以看到第二个贴图，这个是在硬盘中这类HDRI map纹理通用效果。

 

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-012419.jpg)

 

​      Rhino场景可以包含HDR Light Studio多个环境，可以在3D渲染器中自由的多次尝试不同灯光效果。或为不同的相机角度设计不同的灯光。

 

## V-Ray for Rhino Workflow

​       V-Ray 2.0 for Rhino可以与HDR Light Studio直接连接，而不用使用HDR Light Studio的环境纹理Lightmap's。

​      HDR Light Studio可以实时创建、编辑HDRI map。这个是更快更简单的给VRay设计灯光的方法，渲染也更快。

工作流：

​      在场景中创建一个V-Ray Dome灯光。

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-012430.jpg)

 

​      在Dome 灯光的属性面板中有HDR Light Studio的实时控制，在【Light】选项卡下。滚动到属性面板下方看HDR Light Studio Live选项（如果计算机安装了HDR Light Studio）。

 

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-012414.jpg)

 

​      在视窗中打开V-Ray RT显示模式，以便看到场景dome灯光交互与材质实时反馈。

 

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-012428.jpg)

 

​      现在我们可以看到dome light照亮了场景。

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-12421.jpg)

 

​      现在让我们使用HDR Light Studio调整灯光。找到HDR Light Studio Live选项栏控制，按下【Show】按钮开始HDR Light Studio与Dome Light的实时链接。

 

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-012424.jpg)

 

​      HDR Light Studio软件开启，画布的内容会用到V-Ray RT渲染模式。HDR Light Studio中的修改会更新到V-Ray RT。

​      HDR Light Studio提供给V-Ray RT是较小的HDR文件暂存，即使是实时链接，也会自动更新。

 

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-12424.jpg)

 

​      当打开了HDR Light Studio 5，你会看到界面包括它自己的【Render View】面板，加载了一个茶壶模型，当使用HDR Light Studio with V-Ray for Rhino，就没有必要使用这个【Render View】面板，可以关掉。

​      下面是一个很好的例子，在使用V-Ray for Rhino时有更简洁的界面。

 

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-12419.jpg)

 

​      在画布中新增一个灯光，在顶部单击圆形灯光，在画布中间创建一个灯光，你可以看到V-Ray RT更新使用了新灯光。背景的灯光看起来是像素化的，是由于这是使用的是低分辨率，最后再渲染一张高分辨率的HDR文件到硬盘上。

 

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-12427.jpg)

 

​      现在在HDRI map上有一个灯光了， 但是我们如何在模型上正确的位置定位以得到想要的灯光效果呢，答案是使用LightPaint特色，勾选【Light Paint】复选框，你可以直接在V-Ray RT中单击以定位HDR Light Studio中激活的灯光。也可以在Rhino中不使用V-Ray RT渲染模式的其他视图，但是这个会更有效率，可以直接在你眼前看到灯光更新效果。

 

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-012423.jpg)

 

​      现在通过HDR Light Studio中激活的灯光,在V-Ray RT view视图中左键单击3D模型。

 

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-012422.jpg)

 

​      由于LightPaint是Reflection模式，激活的灯光在HDRI map上移动，以使你在模型上点击点的范围是反射，这个你点击点来打灯光技术是非常快速并且准确的方式。

​      在下拉菜单中选择【Rim】模式，这个会直接在HDRI map的背景图像上放置灯光，这个对于创建背光效果，或在你的模型边缘产生轮廓灯。

​      在下拉菜单中选择【Illumination】模式，会定位灯光以照亮你点击的区域，这个是没有反射的不光泽曲面的最好模式。

​      在HDR Light Studio中选择LightPaint模式，在Rhino中单击模型时按住Shift键，例如：在Reflection模式下，Shift键+单击，会高亮显示那个位置产生反射效果的灯光。这是在HDRI map中拾取灯光最好的方式，不用记住灯光名称或位置。

​      在Rhino中选择选择另外一个工具时，Light Paint模式会未激活，直到你再次打开。

​      创建更多的灯光，调整灯光属性直到你满意，单击【Render / Close】按钮，在硬盘上渲染高分辨率的HDR 文件然后会关闭HDR Light Studio，这是灯光阶段最后要做的。

 

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-012412.jpg)

 

​      会弹出HDR Light Studio的【Production Render】对话框，在这里你可以设置HDRI map的分辨率，单击【browse】在硬盘上存储位置，命名文件。单击【Render】按钮，硬盘上会创建文件，V-Ray for Rhino 的dome light会使用这个文件，在渲染完成后会关闭HDR Light Studio。

 

![img](http://ox55f9bg6.bkt.clouddn.com/2017-12-09-012418.jpg)

 

​      现在你的场景会用自定的硬盘上的HDRI 文件照亮，准备生成V-Ray的产品级渲染production rendering。并且这个场景可以被没有安装HDR Light Studio的用户打开，场景用一个标准的HDRI文件格式照亮，完全兼容。

​      HDR Light Studio灯光项目也会嵌入到V-Ray Dome Light in Rhino。保存Rhino场景也会存储灯光设计。下次打开场景时，会为dome light开启HDR Light Studio。灯光会自动加载到Rhino文件保存时的状态。

小贴士：

​      可以在你的犀牛场景创建多个V-Ray Dome Lights并分配给不同的层。这种方式可以在同一个场景中存储许多不同的灯光设计。这在用于创建不同相机视角下不同的照明时很有用。 

​      在HDR Light Studio的Project菜单中保存项目，可以独立于Rhino场景加载灯光项目。可以在项目间调整你喜欢的灯光配置。以这种方式，可以在未来创建一个有用的灯光系列。一旦在HDR Light Studio这样加载灯光，HDR Light Studio当前灯光显示的是你保存和嵌入在你的犀牛的场景的灯光。

 

此教程翻译自HDR Light Studio官方帮助。

 