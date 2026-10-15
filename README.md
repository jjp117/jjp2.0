<h4 align="right">
  <a href="./README_EN.md">English</a>
  <span style="margin:0 10px;color:#24292f">简体中文</span>
</h4>
<p align="center">
<img src="https://jjp-c3e.pages.dev/1.png" width="300"/>
</p>
<h1 align="center">JJP｜自研私有加密容器规范</h1>
<p align="center">
静态网页实现，全部运算在浏览器本地沙箱内执行，用户文件不会上传至任何远端服务器。
</p>
<p align="center">
<a href="https://github.com/jjp117/jjp/releases">
<img src="https://img.shields.io/github/v/release/jjp117/jjp?style=flat-square&logo=github" alt="Release">
</a>
<a href="https://github.com/jjp117/jjp/stargazers">
<img src="https://img.shields.io/github/stars/jjp117/jjp?style=flat-square&logo=github" alt="Stars">
</a>
<a href="https://github.com/jjp117/jjp/blob/main/LICENSE">
<img src="https://img.shields.io/github/license/jjp117/jjp?style=flat-square&logo=github" alt="License">
</a>
</p>
<br>
<p align="center">
<a href="https://jjp-c3e.pages.dev/" target="_blank">
<img src="https://img.shields.io/badge/🔗立即访问‑JJP网页-2563eb?style=for-the-badge&logo=https://jjp-c3e.pages.dev/1.png&logoColor=white" width="320" alt="打开JJP网页">
</a>
&nbsp;&nbsp;
<a href="https://github.com/jjp117/jjp/releases" target="_blank">
<img src="https://img.shields.io/badge/📥下载发行版-red?style=for-the-badge&logo=github&logoColor=white" width="320" alt="下载发行版">
</a>
</p>

# JJP
## 这是什么
JJP 是一种私有容器格式，用于把任意文件封装成一个统一格式的单文件，并对文件内容执行 AES‑GCM 对称加密。密码不会以任何形式存储在生成的文件中，解密所需的密钥由用户密码通过 PBKDF2 派生得到。

## 设计目标
JJP 的设计目标，是为非专业用户提供一种简单、直接、零依赖的文件封装与加密方式。使用者无需安装任何软件、无需配置运行环境、无需掌握命令行，只需通过浏览器即可完成加密与解密。

## 运行方式
JJP 完全运行在浏览器本地。所有加密与解密操作，均通过浏览器内置的 Web Crypto API 完成，不依赖任何后端服务，不上传任何数据，不产生任何网络请求。

## 加密方式
JJP 使用 AES‑GCM 作为加密算法，密钥长度为 256 位。密钥由用户密码通过 PBKDF2 派生，迭代次数为 100,000 次，哈希算法为 SHA‑256。每次加密都会生成新的随机盐值与初始化向量。

## 完整性校验
AES‑GCM 自带认证标签，可在解密时校验数据是否被篡改。若文件被修改、损坏，或密码错误，解密过程将直接失败并返回错误提示，不会输出任何错误内容。

## 格式特性
JJP 为项目自定义私有容器格式，文件结构由作者自行定义，项目仓库附带完整规范文档。它不属于国际通用标准，主流软件无法原生解析`.jjp`文件，只能使用本项目工具进行加解密。

## 使用方式
打开网页版即可使用。用户将文件拖入页面，输入密码，即可生成 JJP 文件；将 JJP 文件拖入页面，输入相同密码，即可还原原始文件。整个过程无需安装、无需注册、无需联网。
> 网页版：https://jjp-c3e.pages.dev/

## ⚠️ 浏览器兼容提示
依赖 Web Crypto API。老旧浏览器（macOS 10.13 Safari 11等）WebCrypto实现存在缺陷，大文件加密会失败。推荐使用新版Chrome、Firefox，或使用PakePlus v0.2.13打包的桌面客户端。

## 安全性说明
JJP 提供的是常规强度的对称加密，能够有效防止文件被随意查看。但 JJP 并非商业级或军事级加密方案，不适合用于保护企业机密、政府数据、金融信息或其他高价值敏感内容。

## 密码管理
JJP 不存储密码，也不提供密码找回功能。密码一旦遗失，文件将无法解密。建议使用者妥善保存密码，并避免将密码与加密文件通过同一条通道发送。

## 适用场景
JJP 适用于个人文件封装、小范围文件分享、非正式场合下的内容保护，以及任何不涉及高价值敏感信息的加密需求。

## 已知限制
- 超大文件在部分老浏览器会内存不足
- AES-GCM单次加密数据存在长度上限
- 解密时必须完整读取整个`.jjp`文件，不支持流式随机读取

## 开源说明
JJP项目主力交付形态为静态网页版；也可使用PakePlus打包为本地桌面客户端，暂无原生CLI命令行版本。网页端代码开源，任何人都可以在浏览器中按 F12 查看页面源代码，了解其实现方式。

## 许可
本项目以 MIT 许可证开源。
