<!-- TOC -->

- [Notes](#notes)
  - [PI4](#pi4)
  - [HTTP](#http)
    - [Cache relation header](#cache-relation-header)
  - [Travisci](#travisci)
  - [YAML](#yaml)
  - [Git](#git)
    - [Semantic Commit Messages](#semantic-commit-messages)
  - [Misc](#misc)
- [Studying](#studying)
  - [AWS](#aws)
    - [Cloudfront](#cloudfront)
    - [ECS capacity provider](#ecs-capacity-provider)
    - [IAM](#iam)

<!-- /TOC -->

## Notes


### PI4

- [Ubuntu mint unoffical](https://github.com/TheRemote/Ubuntu-Server-raspi4-unofficial/releases)

- dd from image to SD

```bash
# List disks
$ diskutil list

# Unmount disk
$ diskutil umountDisk /dev/disk2

$ sudo sh -c 'gunzip -c ~/Desktop/ubuntu-18.04.4.img.xz | sudo dd of=/dev/rdisk2 bs=32m'
```


### HTTP

#### Cache relation header

- [Expires](https://tools.ietf.org/html/rfc7234#section-5.3)

```text
Expires = "Expires" ":" HTTP-date
Expires: Thu, 01 Dec 1994 16:00:00 GMT
```

if [ cache-control: max-age=N && Expires ], expires should be ignored and using $N

- [Cache-control](https://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.9)

Reference: 

[Header Field Definitions](https://tools.ietf.org/html/rfc7234#section-5.2.2)

### Travisci

- [travis.yaml scheme](https://github.com/travis-ci/travis-yml/blob/master/schema.json)

### YAML

<https://yaml.org/spec/1.2/spec.html#id2765878>

- [YAML Parser](http://yaml-online-parser.appspot.com/)

- [YAML 表示多行的寫法](https://stackoverflow.com/questions/3790454/how-do-i-break-a-string-over-multiple-lines/21699210#21699210) 

### Git

```bash
# Checkout branch
$ git checkout BRANCH

# Checkout file
$ git checkout -- FILE/FOLDER
$ git checkout -- .

## Git > 1.25
$ git restore FILE/FOLDER
$ git switch BRANCH

# Show file modification by line
$ git blame FILE

# Rename branch
$ git branch FROM_BRANCH_NAME TO_BRANCH_NAME

# Merge without FF
$ git merge BRANCH --no-ff

# Reset
$ git reset COMMIT_ID
$ git reset HEAD^ --hard
$ git reset

# Add tag
$ git tag TAG_NAME

# Push tag to remote
$ git push origin TAG_NAME

# One line tag and push remote
$ t=TAG_NAME; git tag $t; git push origin $t

# Delete local tag
$ git tag -d TAG_NAME

# Delete remote tag
$ git push --delete origin TAG_NAME

# Delete remote tag(alternative)
$ git push origin :refs/tags/TAG_NAME

# Delete local branch
$ git branch -D BRANCH_NAME

# Delete remote branch
$ git push origin :cat

```

branch: 指向某個 commit id. 每個 branch 佔用 40 bytes. 貼紙概念
HEAD: current branch
git merge branch : 產生一個 commit id 
誰合併誰的差異: 被合併留在原點, 合併會往前

conflict:
修改 conflict 後 git add & git commit

rebase: 把 commit 加在某個 branch 之後

rebase 的好/壞處:
 good: 線圖清楚
 bad: 無法保留歷史紀錄
 常用: 在各自branch頻繁修改後 rebase

reset: 
將 branch reset(become) 回某個 commit
 --mixed 差異檔案進工作目錄(default)
 --soft 差異檔案進暫存區
 --hard 丟掉差異

 ^ : Caret
 ~ : Tilde

 checkout 與 reset 的差異:
	checkout 只移動 HEAD. reset 會移動 HEAD 與 Branch

commit 無法刪除,看不到還是存在

git reflog: 尋找 HEAD log

https://gitbook.tw/

#### [Semantic Commit Messages](https://gist.github.com/joshbuchea/6f47e86d2510bce28f8e7f42ae84c716)

- chore: (updating grunt tasks etc; no production code change)
- docs: (changes to the documentation)
- feat: (new feature for the user, not a new feature for build script)
- fix: (bug fix for the user, not a fix to a build script)
- refactor: (refactoring production code, eg. renaming a variable)
- style: (formatting, missing semi colons, etc; no production code change)
- test: (adding missing tests, refactoring tests; no production code change)

[Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/#summary)

### Misc

[Decrypting SSL/TLS traffic with Wireshark](https://resources.infosecinstitute.com/decrypting-ssl-tls-traffic-with-wireshark/)


## Studying

### AWS

[Building serverless applications with the AWS CDK - and testing them locally](https://sanderknape.com/2019/05/building-serverless-applications-aws-cdk/#displaying-cloudformation-changes)

#### Cloudfront

[This is How I Reduced My CloudFront Bills by 80%](https://medium.com/faun/this-is-how-i-reduced-my-cloudfront-bills-by-80-a7b0dfb24128)

<https://github.com/awsdocs/amazon-cloudfront-developer-guide>

#### ECS capacity provider

Setting existing ecs cluster with capacity provider
<https://gist.github.com/angusfz/0e5b7838a5c4a1ad236700630a5a8dd7>

#### IAM

IAM policy to grant S3 bucket read access

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "s3:GetObject*",
                "s3:GetBucket*",
                "s3:List*"
            ],
            "Resource": [
                "arn:aws:s3:::iamstack-bucket43879c71-mhdl5a3ebzsh",
                "arn:aws:s3:::iamstack-bucket43879c71-mhdl5a3ebzsh/*"
            ],
            "Effect": "Allow"
        }
    ]
}
```