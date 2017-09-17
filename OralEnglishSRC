# coding=utf-8

import requests
import os
from bs4 import BeautifulSoup
import re
import urllib2

base_url = 'http://2d.hep.cn/1722222/'

save_path = r'E:\OralEnglish'
os.mkdir(save_path)
os.chdir(save_path)

for index in range(102):
    index += 1
    index_url = base_url + str(index)


    # 获取资源地址
    def get_url_list():
        response = urllib2.urlopen(index_url)
        html = response.read()
        url = re.findall(r'var u = "(.*?)";', html)
        return url


    # 获取标题
    def get_name():
        response = urllib2.urlopen(index_url)
        html = response.read()
        title = re.findall(r'<title>英语口语新教程：成功交流 /(.*?) \| 高教社二维码资源服务平台</title>', html)
        return title


    # 文件扩展名
    def suf_name():
        response = urllib2.urlopen(index_url)
        html = response.read()
        url = re.findall(r'var u = "(.*?)";', html)
        url1 = str(url)
        suf = url1[-6:-2]
        return suf


    # 下载音频/视频保存到本地
    def get_src(save_path, index_url):
        srcs = get_url_list()
        suf = suf_name()
        name = str(get_name())[3:7]
        for src in srcs:
            res = requests.get(src)
            res.encoding = 'utf-8'
            with open(name + suf, 'wb') as fp:
                fp.write(res.content)


    if __name__ == '__main__':
        get_src(save_path, index_url)






