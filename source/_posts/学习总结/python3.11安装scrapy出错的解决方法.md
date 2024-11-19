---
title: python3.11安装scrapy出错的解决方法
date: 2023-01-31 17:29:00
categories: 编程
tags:
  - python
  - scrapy
---

# python3.11 安装 scrapy 出错的解决方法

jeff 2023-01-31

## 前提

安装最新版 python3.11.1 后，无法安装 scrapy。
`pip install scrapy`

### 出错提示

提示如下：
{% blockquote %}
Collecting certifi>=2017.4.17
Downloading https://mirrors.aliyun.com/pypi/packages/71/4c/3db2b8021bd6f2f0ceb0e088d6b2d49147671f25832fb17970e9b583d742/certifi-2022.12.7-py3-none-any.whl (155 kB)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 155.3/155.3 kB 232.0 kB/s eta 0:00:00
Building wheels for collected packages: twisted-iocpsupport
Building wheel for twisted-iocpsupport (pyproject.toml) ... error
error: subprocess-exited-with-error
× Building wheel for twisted-iocpsupport (pyproject.toml) did not run successfully.
│ exit code: 1
╰─> [5 lines of output]
running bdist_wheel
running build
running build_ext
building 'twisted_iocpsupport.iocpsupport' extension
error: Microsoft Visual C++ 14.0 or greater is required. Get it with "Microsoft C++ Build Tools": https://visualstudio.microsoft.com/visual-cpp-build-tools/
[end of output]
note: This error originates from a subprocess, and is likely not a problem with pip.
ERROR: Failed building wheel for twisted-iocpsupport
Failed to build twisted-iocpsupport
ERROR: Could not build wheels for twisted-iocpsupport, which is required to install pyproject.toml-based projects
{% endblockquote %}

- 安装 scrapy，需要安装其他依赖库。在安装 certifi 过程中，出现提示需要 C++14.0 以上的库，错误导致安装 twisted 失败。根据提示方法安装"Microsoft C++ Build Tools"，会有很多应用程序需要选择安装，无法确定哪个，且安装包过大。安装第三方工具 twisted 后也无法使用。
- 本次安装经历了各种考验，通过百度找到很多方法，有安装 C++的，也有安装 twisted。均没成功。
- 第二天重新尝试后，发现提示是要安装 twisted-iocpsupport，网络中的解决方法都是比较旧，他们的版本还是 python3.2 或者 python3.8，使用的还是 twisted，故无法成功。

## 解决方法

多次尝试得出以下解决方法：

- 1、在https://www.lfd.uci.edu/~gohlke/pythonlibs/#twisted第三方网站下载twisted-iocpsupport对应的包，本机的包为：twisted_iocpsupport‑1.0.2‑pp38‑pypy38_pp73‑win_amd64.whl；
- 2、把文件放在固定目录中，通过 pip install 安装本地包；
- 3、再安装 scrapy，显示安装成功。

## 总结

通过本次教训，得出结论：需要认真看“出错提示”，对比网络答案中所处版本环境与自己环境的差别。
