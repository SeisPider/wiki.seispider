+++
date = "2017-08-02T16:24:01+08:00"
title = "Git commits"
+++
# Function of Commit message
1. Provide more historical information and readly for quickly checking development process.
```bash
git log <last tag> HEAD --pretty=format:%s
```
Above commend can provide brief information of project
2.  Filter information in backtracking development history
```
git log <last release> HEAD --grep feature
```
Above commend can only check the new features
3. Generate Change log directly based on commits.[conventional-changelog](https://github.com/ajoslin/conventional-changelog)

# Format of Commit message
Standard commits are consisted of tree components: Header, Body and Footer
```
<type>(<scope>): <subject>
// 空一行
<body>
// 空一行
<footer>
```
Where Header necessary while body and footer are optional.

## Header
Components: **type**,**scope**,**subject**
1. type: type of commits
```
feat：新功能（feature）
fix：fix bug
docs：documentation
style： 格式（不影响代码运行的变动)
refactor：重构（即不是新增功能，也不是修改bug的代码变动）
test：增加测试
chore：构建过程或辅助工具的变动
```
2. scope: region influenced by commit

3. subject:brief description of purposes
 ```
 Begin with initiative verbs

 First letter in lower case

 without period
 ```
## Body
Detail descriptions of commits
```

More detailed explanatory text, if necessary.  Wrap it to
about 72 characters or so.

Further paragraphs come after blank lines.

- Bullet points are okay, too
- Use a hanging indent
```
[More instroduction](http://www.ruanyifeng.com/blog/2016/01/commit_message_change_log.html)

# Tool
[Commitizen](https://github.com/commitizen/cz-cli) is an efficient tool helping users to write good commits.

## Installation
Dependency: [npm](https://docs.npmjs.com/getting-started/fixing-npm-permissions)
```
npm install -g commitizen
```

## Usage
* go to root directory of your local git repository
```
npm init
```
* After initiation, just run follow commend to apply commitizen for this repository
```
commitizen init cz-conventional-changelog --save --save-exact
```
* Successfully installed, please use git cz rather than git commit
