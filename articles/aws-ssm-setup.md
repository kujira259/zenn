---
title: "System Manager Patch Manager Setup"
emoji: "ð"
type: "tech"
topics: ["aws", "security", "ssm"]
published: false
---
# [WIP] System Manager Patch Manager Setup
## ã¯ããã«

System Manager Patch Managerãç¨ãã¦ããããé©ç¨ããã¾ã§ã®ã»ããã¢ããæé ãè¨è¼

## Agent Install

```bash
sudo yum install -y https://s3.region.amazonaws.com/amazon-ssm-region/latest/linux_amd64/amazon-ssm-agent.rpm
sudo systemctl status amazon-ssm-agent
sudo systemctl enable amazon-ssm-agent
sudo systemctl restart amazon-ssm-agent
sudo systemctl status amazon-ssm-agent
```

## ãã¼ã¹ã©ã¤ã³å®ç¾©

[äºåå®ç¾©ããããã¼ã¹ã©ã¤ã³ãè¡¨ç¤º] ãããã¼ã¹ã©ã¤ã³ãé¸æ

![image](https://user-images.githubusercontent.com/9875633/127068657-d2e3e1df-3fab-423a-9f77-52a9e4331c29.png)

Amazon Linux2ãé¸æ


![image](https://user-images.githubusercontent.com/9875633/127069014-8f2ae4c8-01ad-4e4c-a204-d5d8a2ddcade.png)

![image](https://user-images.githubusercontent.com/9875633/127069117-88de078b-b5fe-4a42-88da-f627c70f0655.png)

ãããã°ã«ã¼ãã®å¤æ´ãããããã°ã«ã¼ããä½æ

## ãããã°ã«ã¼ããä½æ

![image](https://user-images.githubusercontent.com/9875633/127069148-ce63b69f-bc33-47eb-8c6b-8e9a0e5673e6.png)

ãããã°ã«ã¼ãã¯TagãKey[Patch Group]ï¼åºå®ï¼ã«å¯¾ããValueå¤ãå®ç¾©ï¼ããã§ã¯sampleï¼

![image](https://user-images.githubusercontent.com/9875633/127069172-36c35e21-dcef-47fa-a33d-c775c0aeb832.png)

ãããããã¼ã¸ã£ã¼ã®ç»é¢ãããããã°ã«ã¼ããç¢ºèªããã¨ãããã°ã«ã¼ããä½æããã¦ãã

![image](https://user-images.githubusercontent.com/9875633/127069214-2c1c81e6-1d62-4170-b6bb-9a9a5f01944b.png)

## ãããé©ç¨ãè¨­å®

ãããããã¼ã¸ã£ã¼ãããããé©ç¨ãè¨­å®

![image](https://user-images.githubusercontent.com/9875633/127069239-74c3c4f8-8a1d-456f-8cab-1fd360644f2a.png)
ã¡ã³ããã³ã¹ã¦ã£ã³ãã¦ã«è¡ãã¨è¨­å®ããé ç®ãç¢ºèªã§ãã
![image](https://user-images.githubusercontent.com/9875633/127069270-71b6daeb-e484-427c-a96d-0e6ec3979a6f.png)

## ãããé©ç¨å¯¾è±¡ã«IAMè¨­å®

EC2ã«è¨­å®ãã¦ããIAMã«Runcommandãå®è¡ã§ããããã«[**AmazonSSMManagedInstanceCore**] ããªã·ã¼ãå«ãã
![image](https://user-images.githubusercontent.com/9875633/127069288-9c72414e-7163-41e0-a632-32f90c5085ef.png)

ã»ãã·ã§ã³ããã¼ã¸ã£ã¼ããå¯¾è±¡ãè¦ããããã«ãªã

![image](https://user-images.githubusercontent.com/9875633/127068935-855f5ea3-25da-41a6-801b-8d40c7c276b5.png)

â»åã«IAMãã¢ã¿ãããã¦ãªãã¨åºã¦ããªãã®ã§ãSSM Agent ãRestart
