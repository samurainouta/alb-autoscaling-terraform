# ALB + Auto Scaling Terraform ポートフォリオ

このプロジェクトは、Terraform を使用して **AWS 上に EC2 / ALB / Auto Scaling 環境を自動構築** するデモです。  
クラウドエンジニア志望として、ポートフォリオ用に作成しました。

---

## 目的
- Terraform でインフラをコード化する経験を積む
- ALB + Auto Scaling を組み合わせてスケーラブルな環境を構築
- AWS の VPC、Subnet、Security Group などの基本設定を理解

---

## 工夫点 / 学んだこと
- Terraform のリソース依存関係を意識して構築
- Security Group は最小権限で SSH / HTTP アクセスを設定
- ALB のターゲットグループのヘルスチェック設定を理解
- EC2 に自動で Web サーバーをセットアップする方法を学習

---

## 作業手順（スクショ付き）

### 1. VPC と Subnet
作成した VPC と Public Subnet を確認  
Subnet 名：public_a, public_c  
CIDR / AZ が正しいことを確認
![VPCとSubnet](images/vpc_subnet_overview.png)

### 2. Internet Gateway
Public Subnet がインターネットに接続可能か確認
![IGW](images/internet_gateway.png)

### 3. Security Group
EC2 / ALB 用 SG の設定を確認  
SSH / HTTP ルールが正しく反映されていることを示す
![Security Group](images/security_group.png)

### 4. EC2 インスタンス
Terraform で起動した EC2 インスタンス一覧  
Public IP が割り当てられていることを確認
![EC2](images/ec2_instances.png)

### 5. ALB / Listener / Target Group
ALB の Listener と Target Group 設定を確認
![ALB Listener](images/alb_listener.png)

### 6. Terraform Apply 完了
Terraform によるリソース作成が完了
![Apply Complete](images/terraform_apply_complete.png)

### 7. Terraform Destroy 完了
Terraform によるリソース削除が完了
![Destroy Complete](images/terraform_destroy_complete.png)

---

## 注意点 / 今後の改善
- EC2 の HTTP / SSH 設定は必要に応じて変更
- ALB ターゲットが unhealthy になる場合は、EC2 上の Web サーバー設定を確認
- Terraform の `.terraform/` や `.tfstate` ファイルは GitHub にアップロードしていない
