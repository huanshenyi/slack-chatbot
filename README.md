## 説明
Slack対話方AI ChatBot

## 設定ファイル (config.yaml)
account にデプロイ先 AWS アカウントの ID を設定します。
カスタムドメインが不要な場合は domainName, certificateArn をコメントアウトしておきます。
slackBotToken, slackSigningSecret に Slack アプリのトークンを設定します。
OpenAPI Key のマッピングはすべて config.yaml に書いてください。(ソースをちょっと変更しました)
Slack には作成された Lambda function URL (カスタムドメインを設定した場合はその URL) のエンドポイントを指定してください。

## 初期化
```
npx cdk init app --language typescript
```

## デプロイ
1. CDK 用のライブラリをインストール
```
npm install
```
2. デプロイ設定ファイル (config.yaml) を作成
config.example.json のコメントを参考に設定します。

3. CDK 用のブートストラップを実行 (CDK による初回デプロイ時のみ)
```
cdk bootstrap
```
4. デプロイ
```
cdk deploy
```

1. 構成確認
```
npm run cdk:dev synth
```

2. CDK 用のブートストラップを実行
```
npm run cdk:dev bootstrap
```

3. デプロイ
```
npm run cdk:dev deploy
```
4. クリンアップ
```
npm run cdk:dev destroy
```

# Welcome to your CDK TypeScript project

This is a blank project for CDK development with TypeScript.

The `cdk.json` file tells the CDK Toolkit how to execute your app.

## Useful commands

* `npm run build`   compile typescript to js
* `npm run watch`   watch for changes and compile
* `npm run test`    perform the jest unit tests
* `npx cdk deploy`  deploy this stack to your default AWS account/region
* `npx cdk diff`    compare deployed stack with current state
* `npx cdk synth`   emits the synthesized CloudFormation template

## cdk --help
```
  cdk list [STACKS..]             Lists all stacks in the app      [aliases: ls]
  cdk synthesize [STACKS..]       Synthesizes and prints the CloudFormation
                                  template for this stack       [aliases: synth]
  cdk bootstrap [ENVIRONMENTS..]  Deploys the CDK toolkit stack into an AWS
                                  environment
  cdk deploy [STACKS..]           Deploys the stack(s) named STACKS into your
                                  AWS account
  cdk import [STACK]              Import existing resource(s) into the given
                                  STACK
  cdk watch [STACKS..]            Shortcut for 'deploy --watch'
  cdk destroy [STACKS..]          Destroy the stack(s) named STACKS
  cdk diff [STACKS..]             Compares the specified stack with the deployed
                                  stack or a local template file, and returns
                                  with status 1 if any difference is found
  cdk metadata [STACK]            Returns all metadata associated with this
                                  stack
  cdk acknowledge [ID]            Acknowledge a notice so that it does not show
                                  up anymore                      [aliases: ack]
  cdk notices                     Returns a list of relevant notices
  cdk init [TEMPLATE]             Create a new, empty CDK project from a
                                  template.
  cdk context                     Manage cached context values
  cdk docs                        Opens the reference documentation in a browser
                                                                  [aliases: doc]
  cdk doctor                      Check your set-up for potential problems

Options:
  -a, --app                REQUIRED WHEN RUNNING APP: command-line for executing
                           your app or a cloud assembly directory (e.g. "node
                           bin/my-app.js"). Can also be specified in cdk.json or
                           ~/.cdk.json                                  [string]
      --build              Command-line for a pre-synth build           [string]
  -c, --context            Add contextual string parameter (KEY=VALUE)   [array]
  -p, --plugin             Name or path of a node package that extend the CDK
                           features. Can be specified multiple times     [array]
      --trace              Print trace for stack warnings              [boolean]
      --strict             Do not construct stacks with warnings       [boolean]
      --lookups            Perform context lookups (synthesis fails if this is
                           disabled and context lookups need to be performed)
                                                       [boolean] [default: true]
      --ignore-errors      Ignores synthesis errors, which will likely produce
                           an invalid output          [boolean] [default: false]
  -j, --json               Use JSON output instead of YAML when templates are
                           printed to STDOUT          [boolean] [default: false]
  -v, --verbose            Show debug logs (specify multiple times to increase
                           verbosity)                   [count] [default: false]
      --debug              Enable emission of additional debugging information,
                           such as creation stack traces of tokens
                                                      [boolean] [default: false]
      --profile            Use the indicated AWS profile as the default
                           environment                                  [string]
      --proxy              Use the indicated proxy. Will read from HTTPS_PROXY
                           environment variable if not specified        [string]
      --ca-bundle-path     Path to CA certificate to use when validating HTTPS
                           requests. Will read from AWS_CA_BUNDLE environment
                           variable if not specified                    [string]
  -i, --ec2creds           Force trying to fetch EC2 instance credentials.
                           Default: guess EC2 instance status          [boolean]
      --version-reporting  Include the "AWS::CDK::Metadata" resource in
                           synthesized templates (enabled by default)  [boolean]
      --path-metadata      Include "aws:cdk:path" CloudFormation metadata for
                           each resource (enabled by default)          [boolean]
      --asset-metadata     Include "aws:asset:*" CloudFormation metadata for
                           resources that uses assets (enabled by default)
                                                                       [boolean]
  -r, --role-arn           ARN of Role to use when invoking CloudFormation
                                                                        [string]
      --staging            Copy assets to the output directory (use --no-staging
                           to disable the copy of assets which allows local
                           debugging via the SAM CLI to reference the original
                           source files)               [boolean] [default: true]
  -o, --output             Emits the synthesized cloud assembly into a directory
                           (default: cdk.out)                           [string]
      --notices            Show relevant notices                       [boolean]
      --no-color           Removes colors and other style from console output
                                                      [boolean] [default: false]
      --ci                 Force CI detection. If CI=true then logs will be sent
                           to stdout instead of stderr[boolean] [default: false]
      --version            Show version number                         [boolean]
  -h, --help               Show help                                   [boolean]
```