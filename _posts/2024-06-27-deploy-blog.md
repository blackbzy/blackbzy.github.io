---
title: 博客部署
tags:
  - blog
create_date: 2024-06-27
update_date: 2024-06-27
---

> 记录博客的建站和域名选择
{: .prompt-info }

---
# mian
基于：[chirpy](https://chirpy.cotes.page/) Jekyll Theme,黑白主题，简洁，布局我比较中意
## 1.基于github fork创建
环境: **windows11** 
准备工作参考 [Jekyll Docs](https://jekyllrb.com/docs/installation/) 
开始：
- fork出自己的仓库 USERNAME.github.io
- 拉到本地跑cmd：
```sh
bundle
```

遇到报错（已挂节点）
解决方法：
```sh
Could not fetch specs from https://rubygems.org/ due to underlying error
<IO::TimeoutError: Failed to open TCP connection to rubygems.org:443 (Blocking
operation timed out!) 
```
国内外搜索都找不到合理的解决方案，还是gpt解决了问题：
```markdown
1. 检查防火墙
2. 设置代理
3. 更新ssl
4. 使用不同的 gem 源（使用该方法解决问题）
gem sources --add https://gems.ruby-china.com/ --remove https://rubygems.org/
bundle config mirror.https://rubygems.org https://gems.ruby-china.com/
5. 更新 RubyGems
gem update --system
```
- Configuration 配置调整： 
文件_config.yml 根据注释自定义调整
难点一：
comments 评论配置：disqus、giscus国内访问困难，所以选择valine。初版不做太多自定义，目前不支持，所以先不做设置，今后参考[nihil博客](https://nihil.cc/)
- 运行项目：
```sh
# 先安装
bundle add webrick
bundle install
# 再启动
bundle exec jekyll s
```
就此启动成功

## 2.部署github action
如果您已将 `Gemfile.lock` 提交到存储库，并且您的本地计算机未运行 Linux，请转到站点的根目录并更新锁定文件的平台列表：

```
$ bundle lock --add-platform x86_64-linux
```

接下来根据配置github action ，使用默认Jekyll的部署action，然后自动部署成功。

访问页面报错
```
Failed to open TCP connection to rubygems.org:443
```
排查问题和询问gpt排查皆没用。
自己回想改的配置文件哪有问题，发现_config.yml 文件中的url属性应当为默认值，而我配置了github的域名导致访问失败
置空之后保存更新，启动，访问成功
```yml
# Fill in the protocol & hostname for your site.
# e.g. 'https://username.github.io', note that it does not end with a '/'.
url: ""
```

至此博客搭建完成。

## 未完待续
- 双语切换（待定）参考[双语使用方式](https://aursus.github.io/hexo-bilingual)
- 评论服务加上：disqus  valine
- 学习front_end的语言，自己进行theme的调整