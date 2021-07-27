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

[事前定義されたベースラインを表示] からベースラインを選択

![image](https://user-images.githubusercontent.com/9875633/127068657-d2e3e1df-3fab-423a-9f77-52a9e4331c29.png)

Amazon Linux2を選択


![image](https://user-images.githubusercontent.com/9875633/127069014-8f2ae4c8-01ad-4e4c-a204-d5d8a2ddcade.png)

![image](https://user-images.githubusercontent.com/9875633/127069117-88de078b-b5fe-4a42-88da-f627c70f0655.png)

パッチグループの変更からパッチグループを作成

## パッチグループを作成

![image](https://user-images.githubusercontent.com/9875633/127069148-ce63b69f-bc33-47eb-8c6b-8e9a0e5673e6.png)

パッチグループはTagがKey[Patch Group]（固定）に対するValue値を定義（ここではsample）

![image](https://user-images.githubusercontent.com/9875633/127069172-36c35e21-dcef-47fa-a33d-c775c0aeb832.png)

パッチマネージャーの画面からパッチグループを確認するとパッチグループが作成されている

![image](https://user-images.githubusercontent.com/9875633/127069214-2c1c81e6-1d62-4170-b6bb-9a9a5f01944b.png)

## パッチ適用を設定

パッチマネージャーからパッチ適用を設定

![image](https://user-images.githubusercontent.com/9875633/127069239-74c3c4f8-8a1d-456f-8cab-1fd360644f2a.png)
メンテナンスウィンドウに行くと設定した項目が確認できる
![image](https://user-images.githubusercontent.com/9875633/127069270-71b6daeb-e484-427c-a96d-0e6ec3979a6f.png)

## パッチ適用対象にIAM設定

EC2に設定しているIAMにRuncommandが実行できるように[**AmazonSSMManagedInstanceCore**] ポリシーを含める
![image](https://user-images.githubusercontent.com/9875633/127069288-9c72414e-7163-41e0-a632-32f90c5085ef.png)

セッションマネージャーから対象が見えるようになる

![image](https://user-images.githubusercontent.com/9875633/127068935-855f5ea3-25da-41a6-801b-8d40c7c276b5.png)

※先にIAMをアタッチしてないと出てこないので、SSM Agent をRestart
