# Terraformで構築する ALB + Auto Scaling 環境

このプロジェクトは、Terraformを使用してAWS上にALB + Auto Scaling構成を自動構築するデモです。  
VPC、サブネット、セキュリティグループ、ALB、EC2 Auto Scalingを自動的に構成します。

---

## 1️⃣ VPC と Subnet
作成した VPC と Public Subnet を確認できます。

![VPCとSubnet](./images/vpc-subnet.png)

Subnet 名：`public_a`, `public_c`  
CIDR / AZ が正しいことを確認。

---

## 2️⃣ Internet Gateway
Public Subnet がインターネットに接続できる状態を示します。

![Internet Gateway](./images/internet-gateway.png)

IGW が VPC にアタッチされていることを確認。

---

## 3️⃣ Security Group
EC2 と ALB 用のセキュリティグループ設定を確認。

![Security Group](./images/security-group.png)

SSH（22）/ HTTP（80）ルールが正しく設定されていることを確認。

---

## 4️⃣ EC2 インスタンス
Terraform で起動した EC2 インスタンス一覧。

![EC2 Instances](./images/ec2-instances.png)

Public IP が割り当てられていることを確認。

---

## 5️⃣ ALB / Listener / Target Group
ALB の Listener と Target Group 設定画面。

![ALB Listener and Target Group](./images/alb-target-group.png)

ターゲットグループの設定が正しいことを確認。  
自動スケーリングが機能する設定になっていることを確認。

---

## 6️⃣ Terraform Apply 完了
Terraform によるリソース作成が完了した画面。

![Terraform Apply Complete](./images/terraform_apply_complete.png)

`Resources: 5 added, 0 changed, 0 destroyed` が表示されていれば成功です。

---

## 7️⃣ Terraform Destroy 完了
Terraform によるリソース削除が完了した画面。

![Terraform Destroy Complete](./images/terraform_destroy_complete.png)

`Destroy complete! Resources: 5 destroyed.` が表示されていれば、  
AWS上のリソースはすべて削除されています。

---

## ⚙️ 使用技術
- **Terraform v1.x**
- **AWS Provider v5.x**
- **AWS EC2 / ALB / Auto Scaling**
- **Infrastructure as Code (IaC)** による構成管理

---

## ⚠️ 注意事項
- `.terraform/` や `*.tfstate` は Git に含めないように `.gitignore` で除外済み  
- EC2 の HTTP / SSH 設定は必要に応じて変更可能  
- ALB ターゲットが *unhealthy* の場合は、EC2 上の Web サーバー設定を確認  
- `terraform destroy` を忘れずに実行してコストを抑制すること

---

📘 **目的**  
このプロジェクトは、Terraformの基本構文とAWSインフラの構成を理解するための学習用デモです。  
クラウドエンジニア志望者が、インフラ自動化のポートフォリオとして利用できます。


