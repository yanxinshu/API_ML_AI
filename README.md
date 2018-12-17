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
* 需要进行文本录入的人群

### 用户痛点：
* 进行文本录入太麻烦 要逐一输入

### 解决问题
* 进行文本录入可以方便快捷选取文字

## 用户需求
标题|用户案例|重要程度|笔记
:--:|:--:|:--:|:--:
文字识别1|客户要求开发票，发来了截图版的公司全称、税号，商家只能手动输入再开发票|很重要|如果直接选取到文字可以不用手动输入
文字识别2|学生上课时用手机拍ppt内容，回到宿舍想录入电脑进行整理，但是只能一个一个字打进去|很重要|直接识别文字进行归纳整理
文字识别3|企业收集报销单，需要员工把相关内容录入到电脑上进行存档、报销，员工只能一张一张输入|很重要|文字识别方便直接录入


### 产品架构
<p><img src="https://image.ipaiban.com/upload-ueditor-image-20181130-1543567717832012429.png" alt="脑图" title="" /></p>

### 产品原型
<p><img src="https://image.ipaiban.com/upload-ueditor-image-20181201-1543628678892097680.png" alt="原型" title="" /></p>



### API：
调用<p><a href="http://ai.baidu.com/tech/ocr/general">百度API-通用文字识别</a></p>
调用<p><a href="http://wiki.open.qq.com/wiki/%E7%BA%A0%E9%94%99API">腾讯开放平台-文本纠错</a></p>

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
#### 文本纠错示例
``` python
{
        'Action' : 'LexicalCheck',
        'Nonce' : 345122,
        'Region' : 'sz',
        'SecretId' : 'AKIDz8krbsJ5yKBZQpn74WFkmLPx3gnPhESA',
        'Timestamp' : 1408704141,
        'text': '睡交吃饭'
    }
```
``` python
{
        "code": 0,
        "message": "",
        "conf": 1.3,
        "text": "睡觉吃饭",
        "text_annotate": "睡觉吃饭"
    }
```
### 使用比较分析
 华为云通用文字识别图像规格要求高，上传照片经常失败，且URL只能用华为OBS授权的图片，普通百度上的图片URL无法输出

### 风险报告
![price](https://raw.githubusercontent.com/yanxinshu/API_ML_AI/master/much.PNG)
<p><a href="https://cloud.baidu.com/calculator.html#/ocr/price">百度云</a></p>
