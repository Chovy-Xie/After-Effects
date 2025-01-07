# After Effects

> Link. [Shortcut](#AE-Shortcut), [Effects & Presets](#Effects-and-Presets), [Plugin](#AE-Plugins), [漫剪](#漫剪)


## AE Shortcut

> Link. [Tools](#Tools), [Keyflames](#Keyflames), [Comp-Panel](#Comp-Panel), [Layers](#Layers), [3D Camera](#3D-Camera)

### Tools

	A = "Anchor Point"
 	P = "Position"
  	S = "Scale"
   	R = "Rotation"
    T = "Opacity


### Keyflames

	Alt + Shift + (A, P, S, R, T)  # quickly set keyflames
 	U = "Reveal All Keyframed Properties"
  	F9 = "Eases Easy"
   	Ctrl + Click(keyframe)  # remove easing
    Shift + F3  # 关键帧曲线图
	J & K  # jump between keyflames
	I & O  # jump between in_point and out_point

### Comp Panel

	Hold(Space) + Click&Drag  # maneuver around canvas area
 	, & .  # zoom in comp panel
  	Alt + /  # best fit
   	Shift + (Up, Down, Left, Right) = "Move Layer"  # shift --大幅度位移

### Layers

	Ctrl + /  # quick place media
 	Ctrl + Alt + F  # fit to canvas area
  	Ctrl + Shift + Alt + G  # fit to height
   	Ctrl + Shift + Alt + H  # fit to weight
    Hold(Alt) + Drag(media)  # replace media
    Ctrl + Up | Down # 选择上、下一个图层
    Ctrl + [ | ]  # move layers up or down
    (Ctrl + L | R) or (PgUp | PgDn)  # 前进、后退一帧
    (Ctrl + Shift +  L | R) or (Shift + PgUp | PgDn)  # 前进、后退十帧
    
    F2 = "Deselect"
    F3 = "Effects"

	Alt + [ | ]  # 裁剪图层长度
 	Ctrl + D  # 复制图层
  	Ctrl + Shift + D  # split the layer
   	Ctrl + N  # new comp
    Ctrl + K  # reset comp
	Ctrl + Y  # 新建纯色
	Ctrl + Shift + Y  # 重新设置纯色图层
	Ctrl + Alt + Y  # 新建调整图层
	Ctrl + Shift + Alt + Y  # 新建空对象
    Ctrl + Shift + C  # precompose
    Select(蒙版) + Ctrl + T  # 旋转、位移蒙版
    Ctrl + Alt + T  # 时间重映射


### 3D Camera

	Ctrl + Shift + Alt + \  # 对齐选中图层
> [科技效果模板](https://www.vjshi.com/search?st=&wd=%E7%A7%91%E6%8A%80+%E5%9B%BE%E7%89%87)


## AE Plugins

**Flow**：关键帧曲线；

**Motion 4**：模拟真实物理运动；

**Saber**：能量光线效果；

**[Twixtor](#Twixtor-Pro-Setting)**：丝滑补帧#*Twixtor Pro*；

**BCC**：模糊转场，放射光；

**蓝宝石Sapphire**：震动，发光，色散，闪频；

**红巨人Magic Bullet Suite**：滤镜，#*配合s_glow, lumetri, shine, s_rays, 三色调*；

**[Trapcode Suite](#Trapcode-红巨星)**：粒子插件；

**[Optical Flares](#Optical-Flares)**：OP光，#*红眼，刀光，阳光照射效果*；

**FX Console**：效果预设控件#*Ctrl+Space*；

**Deep Glow**：辉光发光插件；


### Twixtor Pro Setting

	# 变速补帧
 	InFPSisOutFPS = (input=8)
	ImagePrep  # Contrast/EdgeEnhance
 	FrameInterp  # Motion_Weighted_Blend
	Warping  # Inverse_w/_SmartBlend
 	MainBGSensitivity  # 100%
	Speed[200:20]  # ~1s


### Trapcode 红巨星

```

```

### Optical Flares

```
Options, Brightness, Scale
```


## Effects and Presets

> Link. [漫画效果](#漫画效果), [生成](#生成), [风格化](#风格化), [透视](#透视), [模糊](#模糊), [扭曲](#扭曲), [过渡](#过渡), [抠像和遮罩](#抠像和遮罩), [调色](#调色), [曲线：细节](#曲线), [弹性表达式](#AE-弹性表达式--S_BlurMoCurves)

### 漫画效果
	S_EdgeDetect(Ctrl+D): {  # 在"原素材"上 = (轨道遮罩 = 亮度&&反转)
 		Edge Smooth: 0.00,
		Brightness: +,
		Saturation: 1.000,
		Threshold: ++,
		Weight Red: *,
		Weight Green: *,
		Weight Blue: *
	}

### 生成
	生成组: {
 		勾画,  # 蒙版路径相关
   		音频频谱 (配合"极坐标=矩形到极线") = (音频层, 起始点, 结束点, 频段, 最大高度, 厚度, 色相插值, 显示选项),  # 根据音频波形制作动态(建立在纯色图层上)
     		无线电波
	}

### 风格化
 	风格化组: {
  		查找边缘, 
    		动态拼贴, 
      		发光 = {A(亮) > B(暗)}
	}

### 透视
  	透视组：{
   		投影,
     		CC Cylinder = {  # 建立圆柱体，例文字立体旋转
       			radius%, 
	  		Rotation, 
     			Light, 
			Shading
		}
	}

### 模糊
 	模糊组：{
  		高斯模糊,  # 纯纯的模糊
    		BCC Gaussian Blur: {Horizontal Blur[0:15:0]},  # 类似高斯模糊
    		径向模糊: { 旋转, 缩放 },
      		CC Radial Fast Blur: { Standard, Brightest, Darkest }  # 光纤放射模糊，类似径向模糊的缩放类型
	}

### 扭曲
 	扭曲组：{
  		边角定位,
    		镜像(需要先预合成): {  # 一般用于航拍，地面天空地面效果
      			中心，
	 		角度: -90
		},
  		CC Page Turn: {  # 翻页效果，操作类似边角定位
    			Back Page={}
		},
  		CC Lens,  # 透过水滴效果，可以用作水滴转场
    		光学补偿  # 反转镜头扭曲(塌陷、穿越、星铁弱点击破效果)
	}

### 过渡
 	过渡组：{
  		百叶窗，  # 一般用于制作背景
    		卡片擦除
	}

### 抠像和遮罩
 	抠像、遮罩组：{
  		提取,  # 提取亮、暗色
    		Keylight(1.2),  # 吸管吸取绿幕
      		简单阻塞工具  # 贴纸描边效果
	}

### 调色
 	调色组：{
  		填充,  # 改色
    		色调 = (黑色={}, 白色={}),
      		三色调 = (高光={}, 中间调={}, 阴影={}),
		曲线 = (黑色, 阴影, 中间调, 高光, 白色),
  		色相/饱和度: {
    			主色调,  # 通道范围：一一对应改色
		},
  		照片滤镜(配合蒙版),  # 局部滤镜效果
    		保留颜色,  # 吸管吸取想要保留的颜色，脱色量[%]
      		更改为颜色: {
			自: {吸管提取}，
   			至: {Customize}
		},
  		Lumtri 颜色 = {
    			基本校正 = {
       				输入 LUT = " ",
	   			颜色 = {色温，色调，饱和度},
       				轻 = {曝光度，对比度，高光，阴影，白色，黑色}
			}，
       			创意 = {Look = " "}，
	  		曲线,  # 同理
     			色轮 = {中间调，阴影，高光}
		}
	}

### 曲线
	# input: 原亮度值
 	# output: 调整后的亮度值
 	曲线(调色)： {  # o(i) = i
  		(0,0): 黑色，
    		(1,1): 阴影,
      		(2,2): 中间调,
		(3,3): 高光,
  		(4,4): 白色
	}
 	# 例: (i,o) = (128,185) -> 整体亮度为128的像素提高到185，其他部分依照曲线做调整
  	# 曝光过高 = 拉低中间调
   	# 增加对比度 = 提亮高光，拉低阴影

     	# 通道 = [R, G, B]
     	光三原色(R, G, B) {
		yellow = R + G
		cyan = G + B  # 青、浅蓝
		magenta = R + B  # 品红
		white = R + G + B
	}
 
	# 针对单一色调进行调整
 	Red = {
		red = R++
		cyan = R--
	}
	Green = {
		green = G++
		magenta = G--
	}
	Blue = {
		blue = B++
		yellow = B--
	}


### AE 弹性表达式  *S_BlurMoCurves*

	amp = 0.1;  # 第一次的强度
	freq = 2;  # 回弹次数
	decay = 4;  # 强度衰减

 	n = 0;
	if (numKeys > 0) {
		n = nearestKey(time).index;
		if (key(n).time > time) { n--; }
	}
	if (n == 0) { t = 0; }
 	else { t = time - key(n).time; }
	if (n > 0) {
		v = velocityAtTime(key(n).time - thisComp.frameDuration/10);
		value + v * amp * Math.sin(freq*t*2*Math.PI) / Math.exp(decay*t);
 	} else { value; }


## 漫剪

### 分镜

	1. 动态拼贴  --去除黑边
 	2. 色相/饱和度  --更改整体色调，用于制作背景
  	3. CC Jaws  --增加整体效果
   	4. roto抠像  --主体人物
	5. 查找边缘  --作用于扣出的人物，可以进行色调更改、湍流效果、发光效果，置于主体下层
	6. 圆圈扩散  --经典漫剪风格


> 参考 [漫剪分镜流程 by 无尽的彼方](https://www.douyin.com/user/self?from_tab_name=main&modal_id=7331275216284290319&showSubTab=favorite_folder&showTab=favorite_collection)


### 排版流程

	roto抠像
 
 	# Ctrl+D
 	roto抠像  # 湍流置换 w/ Deep_Glow
		湍流置换 = {
 			数量：500+，
	 		大小：10~，
	 		偏移(湍流)：y[450:-350]
		}

	文字动画

	背景  # 原画 w/ roto抠像(残影) = 预合成(小屏=Ctrl+Shift+C)
 		原画 = {
			高斯模糊：20~，
			CC Jaws: 60%~
 		}

 	粒子效果(纯色层=Ctrl+Y)  # CC_Particle_World w/ Deep_Glow
		CC Particle World = {
			Producer: {
	 			Radius X: 1.2，
		 		Radius Y: 1，
		 		Radius Z: 1
			}，
	 		Physics: {
				Gravity: -0.25, 
				Extra: 1.1
	 		},
			Particle(Type=Cube || Type=FadedSphere): {
	 			Birth Size: 0.09, 
		 		Death Size: 0.02, 
		 		Size Variation: 0.1%, 
		 		Birth Color: Deep Pink,  #FF1493  || #FF5C60
		 		Death Color: Cyan  #00FFFF
			}
		}

 	OP光(纯色层=Ctrl+Y)  # Optical_Flares w/ S_Rays
		Optical Flares: {
			选择光晕效果：略，
	 		Brightness: 100,
			Scale: 80,
	 		RenderMode: {
				Mode: OnTransparent
	 		},
			Position XY: {
	 			x[i:o], 
		 		y[i:o]
		 	}
		}
		S_Rays: {
			RaysLength: 0.8, 
	 		RaysBrightness: 1, 
			BlurRays: 60, 
	 		Center XY: {
				x[i:o],
				y[i:o]
	 		}
		}

 	Option: {
		调色 = (三色调，曲线，色相/饱和度，照片滤镜#配合蒙版)，
		s_shake: {  # 慢晃效果
			amp: 0.3, 
	 		freq: 0.6, 
			X shake: { XRandAmp: 100 }
		},
		BCC Ripple Dissolve: { speed: Customize },  # 水波纹效果
		变换 = (缩放[0%:100%], 效果不透明度[100%:0%]),  # 灵魂出窍效果
		扫描扫光效果: {
			BCC+Streaks(2s~): {
	 			Blend: Add, 
		 		Vertical Streaks: 0, 
		 		Position[100:0],
		 		Range[0:7:0]
			},
	 		Deep Glow: {
				输入：{ 阈值：99% },
				曝光[0:1:0]
	 		}
		}，
		径向模糊 = (类型=旋转||缩放)，
		玻璃破碎效果(需先预合成=Ctrl+Shift+C)：{
			碎片：{  # Pre-Comp
	 			视图：已渲染，
		 		形状：{
		 			图案：玻璃，
					凸出深度: default
				}，
				作用力 1：{
					半径：0.65+，
		 			强度：default
				},
				物理学：{ 重力：default }
			},
	 		时间重映射(Ctrl+Alt+T): { # 在需要变速的位置打上关键帧，并将最后一帧往后拉 },  # Pre-Comp
			Lumetri 颜色：{
	 			色温：Customize, 
		 		色调：Customize
			}，
	 		发光：{
				发光阈值：Customize,
				发光半径：Customize,
				发光强度：Customize
			},
	 		S_Glow or Deep_Glow = (default)
		}
 	}
	

> 参考 [鬼灭之刃剪辑 by Jexxx.](https://www.douyin.com/user/MS4wLjABAAAA7aMs5WbbRhh_k67TcSSCqn2OGl8el-H5foTbpeHfG3Q?from_tab_name=main&modal_id=7389831599229046068)
