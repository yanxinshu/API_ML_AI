item|content
--|:--:
Target release|2018/11/25
Epic| 识别语音生成课堂实时字幕
Document status|未开始
Document owner|颜信束


# 动机
* 耳背、反应迟钝的同学们/*学渣*许多时候不能第一时间听到/理解老师传达的信息；学生听课效率不高，课后便忘记了上课内容。

# 目标
* 让学渣提升上课体验（学霸也可以）

# 用户
* 大学生

# 解决问题
* 上课一走神便错过重要内容
* 一小节听不懂，导致整节课都听不懂
* 课后翻笔记，发现记得不全

# 用户需求
* 不耽误像往常一样听课
* 不落下任何重点

# 产品功能
* 将课堂中教师说的话实时转换成字幕
* 自动保存音频与匹配字幕

# 产品架构
## 首页
* 为您推荐
## 课表
## 上课
* 开启字幕
* 语言设置

# 产品需求
* 腾讯云实时语音识别API


'''

# -*- coding:utf-8 -*-
# 引用 SDK
import RASRsdk

secret_key = 'kKm26uXCgLtGRWVJvKtGU0LYdWCgOvGP'
secretid = 'AKID31NbfXbpBLJ4kGJrytc9UfgVAlGltJJ8'
appid = '1255628450'
  
# 识别引擎 8k_0 or 16k_0
engine_model_type = '16k_0'
# 结果返回方式 0：同步返回 or 1：尾包返回
res_type = 0
# 识别结果文本编码方式 0:UTF-8,1:GB2312,2:GBK,3:BIG5
result_text_format = 0
#  语音编码方式 1:wav 4:sp 6:skill
voice_format = 1
# 音频文件路径
filepath = "./test.wav"
# 语音切片长度 cutlength<200000
cutlength = 64000
# 调用语音识别函数获得识别结果
RASRsdk.sendVoice(secret_key, secretid, appid, engine_model_type,res_type, result_text_format, voice_format, filepath,cutlength)
'''
