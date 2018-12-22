# API_ML_AI

item|content
--|:--:
Target release|2018/11/25
Epic| 更便捷录入文字
Document status|进行中
Document owner|颜信束


### 动机
* 用户需要提取照片中的内容，不再需要逐一输入，可以快捷拍照取词。
* 若图片不清晰，提取的文字内容可能会有误，可进一步进行文本纠错

### 目标
* 方便提取文字

### 用户
* 需要快捷获取图片内容文字的人群

### 用户痛点：
* 进行文本录入太麻烦 要逐一输入
* 普通文字提取容易出错，要手动更改
* 提取出来的文字不能进一步编辑

### 解决问题
* 快速从图片中提取文字
* 提取文字后进行纠错
* 直接编辑文字

## 用户需求
标题|用户案例|重要程度|笔记
:--:|:--:|:--:|:--:
文字识别|学生上课时用手机拍ppt内容，回到宿舍想录入电脑进行整理，但是只能一个一个字打进去|很重要|直接提取文字进行归纳整理
文本纠错|用软件提取了文字后有些形近字被识别错误，用户需要每一个错字都自己改，很麻烦|很重要|识别错误的片段，给出正确的文本结果
文字编辑|用软件提取文字后，文字没有分隔，要通过打开其他软件进行排版|一般|文字识别方便直接录入


### 产品架构
![yuanxing](https://github.com/yanxinshu/API_ML_AI/blob/master/jiagou.png?raw=true)

### 产品原型
![jiagou](https://github.com/yanxinshu/API_ML_AI/blob/master/yuanxing.png?raw=true)



### API：
调用<p><a href="http://ai.baidu.com/tech/ocr/general">百度API-通用文字识别</a></p>
调用<p><a href="http://ai.baidu.com/docs#/NLP-API/741e48da">首选：百度API-文本纠错</a></p>
调用<p><a href="http://wiki.open.qq.com/wiki/%E7%BA%A0%E9%94%99API">次选：腾讯开放平台-纠错API</a></p>

### 输入/输出

#### 文字识别
* 输入：图片
* 输入：文本

```python
{
	"errno": 0,
	"msg": "success",
	"data": {
		"log_id": "3167391544171532238",
		"direction": 0,
		"words_result_num": 4,
		"words_result": [
			{
				"words": "图像质量检测",
				"probability": {
					"variance": 0.000002,
					"average": 0.999218,
					"min": 0.996165
				}
			},
			{
				"words": "图像美观度与清晰度识别,检测图像色彩、构图以及",
				"probability": {
					"variance": 0.000166,
					"average": 0.99366,
					"min": 0.957218
				}
			},
			{
				"words": "是否存在模糊、失焦、噪点、锯齿、马賽克等情况",
				"probability": {
					"variance": 0.003443,
					"average": 0.985294,
					"min": 0.716799
				}
			},
			{
				"words": "立即使用",
				"probability": {
					"variance": 0,
					"average": 0.999662,
					"min": 0.999385
				}
			}
		]
	}
}
```
#### 文本纠错
* 输入：文本
* 输出：纠正后文本
#### 文本纠错
