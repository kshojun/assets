### EC2
- EC2のinbound ruleだけ開けてもダメ。firewall-cmdでもポートを開ける必要がある
- 停止と終了は全然違う・・。定期的にOSイメージのAMIを作るか、EBSのスナップショットを作っておけば、間違えて終了しても復元できる。
- Terminate Protectionをかけるか、権限ない人はterminateできないようにすべき。

### S3
```php
$this->config = [
    'key'    => $this->accessKey,
    'secret' => $this->secretKey,
    'region' => $this->region,
    'version' => 'latest',
];
```

composerでいれたaws-sdkのversionによって  
```Error retrieving credentials from the instance profile metadata server```
こんなエラーになるので、
```php
$this->config = [
    'region' => $this->region,
    'version' => 'latest',
    'credentials' => [
        'key' => $this->accessKey,
        'secret' => $this->secretKey,
     ],
];
```
- 一括DL   
```aws s3 cp s3://[bucket]/voice . --recursive```

### SES
■SESを利用するために最低限必要なこと  
- お名前.comやRoute53などでメール送信用DNSを設定

- SESで送信用ドメインの認証、送信用メールアドレスの認証を行う

- Amazon SES APIを利用するため、IAMで発行したアクセスキー、シークレットキーが必要
（既に発行済みなので新たに発行する必要はない）

- 新規SESのアカウントの場合は、一日あたり200通まで、1秒あたり1メッセージまでの制限を受ける（SPAM業者対策）
この制限を外すためには申請が必要で、手続きには1日かかる。

- OP25B(Outbound port25 blocking)対策
DNSのAレコードを作成し、AWSに対してEメール送信制限解除リクエストを行う  
↑SESでは25番以外を使うので不要

- EC2で利用するElastic IPがRBL（ブラックリスト）に乗ってる可能性があるので、
次のフォームに必要事項を入力してメール送信制限の解除申請を必要がある
https://portal.aws.amazon.com/gp/aws/html-forms-controller/contactus/ec2-email-limit-rdns-request  
↑SESで対応してくれるので不要。自前でメールサーバーを立てる場合は必要。

- SPF設定

- DKIMの設定

■気を付けるべきこと
- バウンス率は 5% 以下、苦情率は 0.1% 未満に抑える必要がある。  
（バウンスや苦情についてはAmazon SES Metrics から参照できる）

- 上記を守れなかった場合、最大14日間メール送信ができなくなる

■用語説明  
**OP25B(Outbound Port25 Blocking)**  
ISPが25ポートを利用したメール送信を制限すること

**RBL**  
過去にスパムメールを送ったことがあるメールサーバーのブラックリスト

**SPF**  
送信元のIPアドレスが正しいことを証明する仕組み

**DKIMの署名**  
メール送信中に第三者によって改ざんされてないことをISPが証明するため、メールメッセージに署名すること

### CloudFront
■Cache Clear   
- Create Invalidationsで/image/some.png

### AWS CLI
#### install
```bash
curl "https://bootstrap.pypa.io/get-pip.py" -o "get-pip.py"
sudo python get-pip.py
sudo pip install awscli
```
#### setting
```bash
aws configure
AWS Access Key ID [None]: 
AWS Secret Access Key [None]: 
Default region name [None]: そのまま
Default output format [None]: そのまま
```

#### command
```bash
 aws s3 ls
 ```

