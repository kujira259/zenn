# [WIP] System Manager Patch Manager Setup
## はじめに

System Manager Patch Managerを用いてパッチを適用するまでのセットアップ手順を記載

## Agent Install

```bash
sudo yum install -y https://s3.region.amazonaws.com/amazon-ssm-region/latest/linux_amd64/amazon-ssm-agent.rpm
sudo systemctl status amazon-ssm-agent
sudo systemctl enable amazon-ssm-agent
sudo systemctl restart amazon-ssm-agent
sudo systemctl status amazon-ssm-agent
```

## ベースライン定義

![image-20210726204721163](C:\Users\koichi.tsuyama\AppData\Roaming\Typora\typora-user-images\image-20210726204721163.png)

[事前定義されたベースラインを表示] からベースラインを選択

![image-20210726204936492](C:\Users\koichi.tsuyama\AppData\Roaming\Typora\typora-user-images\image-20210726204936492.png)

Amazon Linux2を選択

![image-20210727055808325](C:\Users\koichi.tsuyama\AppData\Roaming\Typora\typora-user-images\image-20210727055808325.png)

パッチグループの変更からパッチグループを作成

## パッチグループを作成

![image-20210727055927760](C:\Users\koichi.tsuyama\AppData\Roaming\Typora\typora-user-images\image-20210727055927760.png)

パッチグループはTagがKey[Patch Group]（固定）に対するValue値を定義（ここではsample）

![image-20210727055946713](C:\Users\koichi.tsuyama\AppData\Roaming\Typora\typora-user-images\image-20210727055946713.png)

パッチマネージャーの画面からパッチグループを確認するとパッチグループが作成されている

![image-20210727062354089](C:\Users\koichi.tsuyama\AppData\Roaming\Typora\typora-user-images\image-20210727062354089.png)

## パッチ適用を設定

パッチマネージャーからパッチ適用を設定

![image-20210727062605335](C:\Users\koichi.tsuyama\AppData\Roaming\Typora\typora-user-images\image-20210727062605335.png)

メンテナンスウィンドウに行くと設定した項目が確認できる

![image-20210727071348823](C:\Users\koichi.tsuyama\AppData\Roaming\Typora\typora-user-images\image-20210727071348823.png)

## パッチ適用対象にIAM設定

EC2に設定しているIAMにRuncommandが実行できるように[**AmazonSSMManagedInstanceCore**] ポリシーを含める

![image-20210727072054130](C:\Users\koichi.tsuyama\AppData\Roaming\Typora\typora-user-images\image-20210727072054130.png)

セッションマネージャーから対象が見えるようになる

![image-20210727072836801](C:\Users\koichi.tsuyama\AppData\Roaming\Typora\typora-user-images\image-20210727072836801.png)

※先にIAMをアタッチしてないと出てこないので、SSM Agent をRestart