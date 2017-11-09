---
layout: post

title: "在Windows下体验headless chrome for python"
date: 2017-11-06 22:23:30 +0800

categories: post
tags: [python]
---

>环境配置
```
windows 10
python 3.6
chrome 60
```

>实现python 截图,  代码来源自 [https://gist.github.com/rverton/d07a2232f4c0e1c2b9894e9bdb4fa6cf](https://gist.github.com/rverton/d07a2232f4c0e1c2b9894e9bdb4fa6cf)

1. 安装chrome (版本号最好高于59)

2. 使用pip安装 `selenium`
```bash
pip install selenium
```

3. 下载 `WebDriver for Chrome`, 下载地址 [https://sites.google.com/a/chromium.org/chromedriver/downloads](https://sites.google.com/a/chromium.org/chromedriver/downloads)

4. 修改`CHROME_PATH`和`CHROMEDRIVER_PATH`, 运行代码:

```python
'''
python 页面截图
'''

from optparse import OptionParser

from selenium import webdriver
from selenium.webdriver.chrome.options import Options

CHROME_PATH = 'C:\Program Files (x86)\Google\Chrome\Application\chrome.exe'  # chrome地址
CHROMEDRIVER_PATH = 'C:\chromedriver_win32\chromedriver.exe'  # chromedriver 地址
WINDOW_SIZE = "1920,1080"  # 窗口大小

chrome_options = Options()  
chrome_options.add_argument("--headless")  
chrome_options.add_argument("--window-size=%s" % WINDOW_SIZE)
chrome_options.binary_location = CHROME_PATH

def make_screenshot(url, output):
    # if not url.startswith('http'):
    #     raise Exception('URLs need to start with "http"')

    driver = webdriver.Chrome(
        executable_path=CHROMEDRIVER_PATH,
        chrome_options=chrome_options
    )  
    driver.get(url)   # 获取内容
    driver.save_screenshot(output)  # 内容保存为快照
    driver.close()

if __name__ == '__main__':
    url = "http://www.baidu.com"
    path = "./screenshot.png"

    make_screenshot(url, path)
```
