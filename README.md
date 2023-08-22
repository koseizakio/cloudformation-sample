# Cloudformation サンプル

Cloudformationは、AWSのクラウドリソースを構成および管理するためのサービスです。CloudFormationテンプレートと呼ばれるテキストファイルを使用して、AWSリソースを定義し、プロビジョニングすることができます。CloudFormationテンプレートは、JSONまたはYAMLで記述できます。

- AWSリソースを定義し、プロビジョニングする
- AWSリソースのライフサイクルを管理する
- AWSリソースの構成を再現する
- AWSリソースの変更を自動化する

ここでは、YAML形式でサンプルを出す。

### cfn-lintインストール

- CloudformationのYAMLの文法を確認するために実行する。

- https://formulae.brew.sh/formula/cfn-lint

### cfn-lint実行

```
cfn-lint vpc.yaml
```

### AWS CLIをMacでインストール

[AWS CLIのインストール方法](https://zenn.dev/akakuro/articles/30f570b8863bef)

### AWS CLIでCloudformaion実行する

検証

```
aws cloudformation validate-template --template-body file://vpc.yaml
```

```
aws cloudformation validate-template --template-body file://ec2.yaml
```

```
aws cloudformation validate-template --template-body file://rds.yaml
```

```
aws cloudformation validate-template --template-body file://elb.yaml
```

実行

```
aws cloudformation create-stack --stack-name handson-cfn --template-body file://vpc.yaml
```

```
aws cloudformation create-stack --stack-name handson-cfn-ec2 --template-body file://ec2.yaml
```

```
aws cloudformation create-stack --stack-name handson-cfn-rds --template-body file://rds.yaml
```

```
aws cloudformation create-stack --stack-name handson-cfn-elb --template-body file://vpc.yaml
```

### CloudformationのYAMLファイルについて

- [VPCのYAML](./cloudformation/vpc.yaml) 

VPCにてap-northeast-1aとap-northeast-1cのパプリックサブネットとプライベートサブネットの仮想ネットワーク構築
- [EC2のYAML](./cloudformation/ec2.yaml)

EC2一台構築

- [RDSのYAML](./cloudformation/rds.yaml)

RDS一台構築

- [ELBのYAML](./cloudformation/elb.yaml)

ap-northeast-1aとap-northeast-1cのロードバランサー構築

- [S3のYAML](./cloudformation/s3-webhosting.yaml)

S3で静的サイトホスティングする用のCloudformation