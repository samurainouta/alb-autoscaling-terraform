# ALB + Auto Scaling Terraform Project

このプロジェクトは、Terraform を使って AWS 上に以下を構築するデモです。

- VPC と Public Subnet
- Internet Gateway
- Security Group（EC2 / ALB）
- EC2 インスタンス（Auto Scaling）
- ALB (Application Load Balancer) と Listener / Target Group

---

## 1. VPC と Subnet

作成した VPC と Public Subnet を確認できます。

![VPCとSubnet](vpc_subnet_overview.png)

- Subnet 名：public_a, public_c
- CIDR / AZ が正しいことを確認

---

## 2. Internet Gateway

Public Subnet がインターネットに接続できる状態を示します。

![Internet Gateway](internet_gateway.png)

- IGW が VPC にアタッチされていることを確認

---

## 3. Security Group

EC2 と ALB 用のセキュリティグループ設定を確認。

![Security Group](security_group_rules.png)

- SSH / HTTP ルールが正しく設定されていることを確認

---

## 4. EC2 インスタンス

Terraform で起動した EC2 インスタンス一覧。

![EC2 Instances](ec2_instances.png)

- Public IP が割り当てられていることを確認

---

## 5. ALB / Listener / Target Group

ALB の Listener と Target Group 設定画面。

![ALB Listener / Target Group](alb_listener_targetgroup.png)

- ターゲットグループの設定が正しいことを確認
- 自動スケーリングが機能する設定になっていることを確認

---

## 6. Terraform Apply 完了

Terraform によるリソース作成が完了した画面。

![Terraform Apply Complete](terraform_apply_complete.png)

- `Resources: 5 added, 0 changed, 0 destroyed` が表示されていることを確認

---

## 7. 注意事項

- EC2 の HTTP / SSH 設定は必要に応じて変更
- ALB ターゲットが `unhealthy` の場合は EC2 上の Web サーバー設定を確認
- このプロジェクトでは Terraform の環境ファイル（`.terraform/`）や `.tfstate` は GitHub にアップロードしない

---

## 8. 使用技術

- Terraform
- AWS VPC / Subnet / IGW / Security Group
- EC2 / Auto Scaling
- ALB / Target Group
