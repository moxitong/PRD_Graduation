# API_ML_AI/毕业纪念APP

|   产品名字  |   明年今日  |
| --- | --- |
|    文件主人 |   莫熙彤  |
|    文件设计者 |  莫熙彤   |

## PRD 价值主张设计 15%

### PRD1.加值宣言 3%
经过调查，市面上的毕业纪念册大多都是由学校统一印刷到本上的，不能根据每个人的情况自行选择照片，也不能随身携带随时查看，还容易丢失。针对上述缺点，我们团队将为毕业生们提供一个电子版的专门毕业纪念的平台，方便用户保存照片，随时查看，免除了照片丢失的风险；同时，有区分度地排列被拍摄者的照片数量，自动整理成对应的相册集；尽力实现照片与声音双结合，保存两种感官感觉以加深纪念价值。

### PRD2.核心价值（MVP） 3%
1.能通过智能算法推算出相册主人及被拍摄者的亲密度关系，进行智能分类

2.通过人脸识别API为照片中的人物打上标签，点击人物可显示标签信息

3.能根据亲密度排行自动整理出影像集并播放

4.能实时保存下身边好友的留言录音并转化为文字

### PRD3.核心价值与用户痛点 3%

1.传统的纸质版毕业纪念册不方便携带；不能自行挑选照片；容易破损或丢失

2.同学信息不能及时保持更新

3.想要的照片过多，传统纸质版毕业相册无法满足用户需求

4.相片过多而难以挑选到包含自己的好看的照片

5.毕业纪念册通常只能看得见照片而无法保留声音信息

### PRD4.人工智能概率性与用户痛点 3%

* 人脸识别（Azure）

人脸图像过小会影响识别效果，人脸图像过大会影响识别速度。非专业人脸识别摄像头常见规定的最小识别人脸像素为60*60或100*100以上；在规定的图像大小内，算法更容易提升准确率和召回率；图像大小反映在实际应用场景就是人脸离摄像头的距离；过曝或过暗的光照环境都会影响人脸识别效果。根据阿里云提供的数据，除去特殊情况外，他们的人脸api精度>98%，这种概率符合被用户接收的最低标准。

* 实时语音转写（阿里云）

在拍摄过程中因为人员过多可能无法清晰录入到正在说话人的完整音频，或者出现因为口音不同而出现的文字转写错误。阿里云的实时语音转写api使用了国内独创的字级LC-BLSTM/DFSMN-CTC建模，相对业界传统CTC方法降低了20%的错误率，大幅提高了语音识别的精度。

* 情感分析（Azure）

在人脸检测定位返回结果的基础上，识别各个检测人脸的四种属性，返回性别（男/女）、年龄、表情（笑/不笑）、眼镜（戴/不戴）；并可返回人脸的1024维深度学习特征，基于这个特征并按照我们给出的特征比较规则，用户可实现高性能的人脸识别，该算法在业内公开测试集lfw上达到了99.58%的识别精度。

### PRD5.需求列表与人工智能API加值 3%

#### 需求列表

|   用户需求  |   对应标题  |  重要程度  |
| ----- | ----- | ----- |
|   在手机上方便快捷地查看纪念相册 |   查看  |  重要  |
|   查看系统推荐的相册集或自己分类的相册集 |  相册集   |  重要  |
|  回忆当时的留言或者录音片段  |  相册的语音播放键  |  次重要  |

#### 人工智能API加值
- 1.阿里云 人脸识别API

价值宣言：人脸识别（Face Recognition）基于图像或视频中的人脸检测、分析和比对技术，提供人脸检测定位、人脸属性识别和人脸比对等独立服务模块。可以为开发者和企业提供高性能的在线API服务，应用于人脸AR、人脸识别和认证、大规模人脸检索、照片管理等各种场景。

阿里云的人脸识别api识别精度高，千人注册级别，精度>98%，能够很好的适应本产品对于人脸识别精确度的需求；同时，阿里云的人脸识别支持多平台，CPU、GPU计算模式，灵活部署，为产品以后的扩展提供了可实现性

- 2.微软Azure 情感API

价值宣言：Face API可检测图像中的人脸並返回其位置的矩形坐标。同样地，面部检测可以提取一系列与面部相关的属性。例如，头部姿势，性別，年龄，情绪，面部毛发和眼镜。

微软Azure的这款api可以精确地识别出相片中人物的特征以及情绪，对于本产品中分析被拍摄者亲密度的功能有所帮助；其中所包含的人脸分组以及人员识别的功能对本产品中的自动图形标记很有用。

- 3.阿里云 实时语音转写API

价值宣言：对不限时长的音频流做实时识别，达到“边说边出文字”的效果，内置智能断句，可提供每句话开始结束时间。可用于视频实时直播字幕、实时会议记录、实时法庭庭审记录、智能语音助手等场景。

毕业纪念不应该只有简单的图片，令图片加上声音或者文字的辅助能够更好地保存下当时的回忆。阿里云的这款api能够进行实时的语音转写，在保留了录音的同时能够马上转化为文字，帮助使用者留下精彩的回忆瞬间。

## 原型 20%
## API 产品使用关键AI或机器学习之API的输出入展示 15%
### API1.使用水平 5%

1.人脸比对，判断是否为同一个人（阿里云 人脸识别API）
[点击此处体验阿里云ET体验馆](https://data.aliyun.com/ai?spm=5176.12127906.1357642..75e7cf823TWtL9#/face-comparison)

- 输入：随意两张照片的url地址

![邓紫棋1](https://gitee.com/NFUNM066/first/raw/master/%E9%82%93%E7%B4%AB%E6%A3%8B1.png)
![邓紫棋2](https://gitee.com/NFUNM066/first/raw/master/%E9%82%93%E7%B4%AB%E6%A3%8B2.png)

- 输出：结果显示是否为同一个人

如果检测通过确定是同一个人则会显示
![人脸比对](https://gitee.com/NFUNM066/first/raw/master/%E4%BA%BA%E8%84%B8%E6%AF%94%E5%AF%B9.png)
如果不是同一个人则会显示
![不是同一人](https://gitee.com/NFUNM066/first/raw/master/%E4%B8%8D%E6%98%AF%E5%90%8C%E4%B8%80%E4%BA%BA.png)


2.识别被摄者情感信息（微软Azure 情感API）

- 输入：照片url地址

```

import requests
import json

subscription_key = '8da6e0d5d7264123a6006287d2f29b13'   # 这里使用用户自己申请的Key
assert subscription_key

face_api_url = 'https://westcentralus.api.cognitive.microsoft.com/face/v1.0/detect'

image_url = 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1568229125854&di=4408ac30928b6d4b86be57a5ccdf3601&imgtype=0&src=http%3A%2F%2Fb-ssl.duitang.com%2Fuploads%2Fitem%2F201510%2F02%2F20151002220517_aWtBm.jpeg'      # 这里贴上相片链接

headers = {'Ocp-Apim-Subscription-Key': '8da6e0d5d7264123a6006287d2f29b13'}

params = {
    'returnFaceId': 'true',
    'returnFaceLandmarks': 'false',
    'returnFaceAttributes': 'age,gender,headPose,smile,facialHair,glasses,emotion,hair,makeup,occlusion,accessories,blur,exposure,noise',
}

response = requests.post(face_api_url, params=params,
                         headers=headers, json={"url": image_url})
print(json.dumps(response.json()))

```

- 输出：照片所包含的人物信息（包括情感、面部表情、头发颜色等细节）

```

[{"faceId": "1197910c-c37c-49bc-9c52-2bc14cbffead", "faceRectangle": {"top": 171, "left": 463, "width": 249, "height": 249}, 
"faceAttributes": {"smile": 1.0, "headPose": {"pitch": -6.6, "roll": 2.7, "yaw": 2.1}, "gender": "female", "age": 21.0, "facialHair": 
{"moustache": 0.0, "beard": 0.0, "sideburns": 0.0}, "glasses": "NoGlasses", "emotion": {"anger": 0.0, "contempt": 0.0, "disgust": 0.0, 
"fear": 0.0, "happiness": 1.0, "neutral": 0.0, "sadness": 0.0, "surprise": 0.0}, "blur": {"blurLevel": "low", "value": 0.0}, "exposure": 
{"exposureLevel": "goodExposure", "value": 0.68}, "noise": {"noiseLevel": "low", "value": 0.08}, "makeup": {"eyeMakeup": true, 
"lipMakeup": true}, "accessories": [], "occlusion": {"foreheadOccluded": false, "eyeOccluded": false, "mouthOccluded": false}, "hair": 
{"bald": 0.02, "invisible": false, "hairColor": [{"color": "red", "confidence": 0.96}, {"color": "other", "confidence": 0.92}, {"color": 
"blond", "confidence": 0.51}, {"color": "gray", "confidence": 0.16}, {"color": "brown", "confidence": 0.15}, {"color": "black", 
"confidence": 0.09}]}}}]

```

3.实时留言板功能（阿里云 实时语音转写API）
[点击此处体验实时语音转写功能](https://ai.aliyun.com/nls/trans?spm=a2c4g.11186623.h2v3icoap.181.4f925fdbK6gzUj)

- 输入：点击“开启录音”，对着麦克风说话


