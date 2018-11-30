item|content
--|:--:
Target release|2018/11/25
Epic| 易录APP
Document status|进行中
Document owner|颜信束


# 动机
* 用户需要提取照片中的内容，不再需要逐一输入，可以快捷拍照取词。

# 目标
* 方便提取文字，简化用户体验

# 用户
* 需要进行文本录入的人群。

# 用户痛点：
* 进行文本录入太麻烦了要逐一输入

# 解决问题
* 进行文本录入可以方便快捷选取文字。

# 用户需求
标题|用户案例|重要程度|笔记
:--:|:--:|:--:|:--:
文字识别1|客户要求开发票，发来了截图版的公司全称、税号，商家只能手动输入再开发票|很重要|如果直接选取到文字可以不用手动输入
文字识别2|学生上课时用手机拍ppt内容，回到宿舍想录入电脑进行整理，但是只能一个一个字打进去|很重要|直接识别文字进行归纳整理
文字识别3|企业收集报销单，需要员工把相关内容录入到电脑上进行存档、报销，员工只能一张一张输入|很重要|文字识别方便直接录入

# 产品功能
* 把图片内的文字内容进行提取

# 产品架构
<p><img src="https://image.ipaiban.com/upload-ueditor-image-20181130-1543567717832012429.png" alt="脑图" title="" /></p>


## API：
调用<p><a href="http://ai.baidu.com/tech/ocr/general">百度API-通用文字识别</a></p>
调用<p><a href="http://ai.baidu.com/tech/nlp/text_corrector">百度API-文本纠错</a></p>

···html
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
···
