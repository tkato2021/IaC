ブログの構成図（マネージドコンソールで作成）をもとにCloudFormationでコード化<br>
https://note.com/etudier_noter/n/n05c0c2aeb3f8<br>
<br>
1.マネージドコンソールで作成した時と異なる点<br>
・VPCとサブネットのセグメント<br>
・EC2のバージョン<br>
・ドメインはサブドメインを使用<br>
　※マネージドコンソールで作成時の構成を保持したまま実施したいため<br>
<br>
2.各ファイルと実行順番<br>
各ファイルにて、主に何を実行しているかを記載しています。<br>
実行順番は項番通りになります。<br>
<br>
①VPC.yml<br>
VPC、IGW、ルーティングテーブルを記載<br>
<br>
②SecurityGroup.yml<br>
EC2、RDS、ALBのセキュリティグループを記載<br>
<br>
③S3_IAM-Role.yml<br>
EC2からS3に対してアクセスを許可するIAMロールを記載<br>
<br>
④EC2.yml<br>
起動テンプレートでユーザーデータ作成、EC2インスタンス指定、Elastic IP<br>
EC2へのSSH接続のためのセキュリティグループを記載<br>
AMI:Amazon Linux 2 AMI 2.0.20220121.0 x86_64 HVM gp2,ami-0e3861265a3a335cc<br>
<br>
⑤RDS.yml<br>
DBインスタンス指定、サブネットグループ、パラメータグループを記載<br>
MySQL Version：8.0.26を指定<br>
<br>
⑥ALB.yml<br>
ALB、ターゲットグループ、リスナー、EC2へのSSH接続のためのセキュリティグループを記載<br>
Route53にて既存ホストゾーン下にサブドメイン作成、AWS Certificate Managerで証明書発行を記載<br>
<br>
⑦S3.yml<br>
バケット作成を記載<br>
<br>
