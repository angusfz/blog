---
tags: travisci
categories: CI/CD

---

<p>Issue desc :  在 TravisCI 使用 Build lifecycle: before_deploy, 遇到會執行多次的問題.</p>
<p>Resolution:<br>
根據<a href="https://docs.travis-ci.com/user/customizing-the-build#Deploying-your-Code">Travis文件</a><br>
<code>before_deploy</code> and <code>after_deploy</code> 會在 deploy  provider前後執行.<br>
所以多個 deploy provider (S3 + Codedeploy) 就會造成執行多次.<br>
改用<code>after_success</code> 後解決.</p>
<p>Ref:<br>
<a href="https://docs.travis-ci.com/user/customizing-the-build#Deploying-your-Code">https://docs.travis-ci.com/user/customizing-the-build#Deploying-your-Code</a></p>

