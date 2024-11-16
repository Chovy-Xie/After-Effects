# After Effects
> Note. Shortcut, Effects & Presets, Plugin, 漫剪

## Content
[AE Shortcut](#AE-Shortcut)

[AE Plugins](#AE-Plugins)

[Effects and Presets](#Effect-and-Presets)

[漫剪](#漫剪)

## AE Shortcut

### Tools

**A**=<ins>Anchor Point</ins>

**P**=<ins>Position</ins>

**S**=<ins>Scale</ins>

**R**=<ins>Rotation</ins>

**T**=<ins>Opacity</ins>


### 3-D Camera

> [科技效果模板](https://www.vjshi.com/search?st=&wd=%E7%A7%91%E6%8A%80+%E5%9B%BE%E7%89%87)


## AE Plugins

**Flow**：关键帧曲线；

**Motion 4**：模拟真实物理运动；

**Saber**：能量光线效果；

**[Twixtor](#Twixtor-Pro-Setting)**：丝滑补帧#*Twixtor Pro*；

**BCC**：模糊转场，放射光；

**蓝宝石Sapphire**：震动，发光，色散，闪频；

**红巨人Magic Bullet Suite**：滤镜，#*配合s_glow, lumetri, shine, s_rays, 三色调*；

**Trapcode Suite**：粒子插件；

**Optical Flares**：OP光，#*红眼，刀光，阳光照射效果*；

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


## Effects and Presets

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
		 		Birth Color: Deep Pink,  #FF1493
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
