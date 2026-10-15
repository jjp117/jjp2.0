<h4 align="right">
  <a href="./README.md">简体中文</a>
  <span style="margin:0 10px;color:#24292f">English</span>
</h4>

<p align="center">
<img src="https://123-a2r.pages.dev/1.png" width="300"/>
</p>

<h1 align="center">JJP｜Proprietary Encrypted Container Specification</h1>

<p align="center">
Implemented as static web page. All computations run locally inside browser sandbox. No user files are uploaded to remote servers.
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
<a href="https://123-a2r.pages.dev/" target="_blank">
<img src="https://img.shields.io/badge/🔗Open‑JJP_Web‑2563eb?style=for‑the‑badge&logo=googlechrome&logoColor=white" width="320" alt="Open JJP Web">
</a>
&nbsp;&nbsp;
<a href="https://github.com/jjp117/jjp/releases" target="_blank">
<img src="https://img.shields.io/badge/📥Download‑Desktop_Build‑2ea44f?style=for‑the‑badge&logo=windows&logoColor=white" width="320" alt="Download Client">
</a>
</p>

# JJP
## What is this
JJP is a proprietary container format designed to encapsulate arbitrary files into a single unified file, and to apply AES‑GCM symmetric encryption to the file content. The password is never stored in the generated file in any form. The decryption key is derived from the user's password via PBKDF2.

## Design goal
The design goal of JJP is to provide a simple, direct, and zero‑dependency file encapsulation and encryption method for non‑professional users. Users do not need to install any software, configure any runtime environment, or master the command line. Encryption and decryption can be completed entirely within a browser.

## How it runs
JJP runs entirely locally in the browser. All encryption and decryption operations are performed through the browser's built‑in Web Crypto API. It does not rely on any backend service, does not upload any data, and does not generate any network requests.

## Encryption
JJP uses AES‑GCM as the encryption algorithm, with a key length of 256 bits. The key is derived from the user's password via PBKDF2, with 100,000 iterations and SHA‑256 as the hash algorithm. A new random salt and initialization vector are generated for every encryption.

## Integrity verification
AES‑GCM includes an authentication tag, which can verify whether the data has been tampered with during decryption. If the file has been modified, corrupted, or the password is incorrect, the decryption process will fail immediately and return an error message, without outputting any incorrect content.

## Format characteristics
JJP is a proprietary format. The file structure is defined by the author of this project, and the complete specification is not publicly disclosed. Since the format is not included in any public standard and is not compatible with any existing software, external tools cannot directly identify, parse, or open JJP files.

## Usage
Open the web version and use it directly. Users drag a file into the page and enter a password to generate a JJP file. To restore the original file, drag the JJP file into the page and enter the same password. The entire process requires no installation, no registration, and no internet connection.

> Web version: https://123‑a2r.pages.dev/

## Security note
JJP provides symmetric encryption of conventional strength, which can effectively prevent files from being casually viewed. However, JJP is not a commercial‑grade or military‑grade encryption solution. It is not suitable for protecting corporate secrets, government data, financial information, or other high‑value sensitive content.

## Password management
JJP does not store passwords and does not provide password recovery. Once the password is lost, the file cannot be decrypted. Users are advised to keep their passwords safe and avoid sending the password and the encrypted file through the same channel.

## Use cases
JJP is suitable for personal file encapsulation, small‑scale file sharing, content protection in informal settings, and any encryption needs that do not involve high‑value sensitive information.

## Open source note
The web version of JJP is publicly accessible. Anyone can press F12 in the browser to view the page source code and understand its implementation. The project does not provide standalone distribution files or a command‑line version. All functionality is delivered in the form of a web page.

## License
This project is open‑sourced under the MIT License.
