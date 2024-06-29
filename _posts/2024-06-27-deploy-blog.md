---
title: 博客部署
tags:
  - blog
create_date: 2024-06-27
update_date: 2024-06-27
---
# summary
>[!info]
>

---
# mian
基于：[chirpy](https://chirpy.cotes.page/) Jekyll Theme,黑白主题，简洁，布局我比较中意
## 1.开始 基于github fork创建
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


---
故事未完:179
