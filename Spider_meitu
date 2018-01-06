#encoding = utf-8

import requests
import os
import re


#打开url获取response
def url_open(url):

    header = {'User-Agent':"Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) "
                           "Chrome/49.0.2623.221 Safari/537.36 SE 2.X MetaSr 1.0"
              }
    response = requests.get(url, headers = header)
    return response

#找到页面中的图片地址，返回图片地址的列表
def find_imgs(url):

    html = url_open(url).text
    pir = r'img .*? src="(.+?\.jpg)"'
    img_addrs = re.findall(pir, html)
#    print(img_addrs)
    return img_addrs

def download_imgs(folder='MeiTu'):

    os.mkdir(folder)
    os.chdir(folder)

#设置起始爬取页面
# 自命名图片,从0开始
    x = 0
#设置爬取起始页面（从1开始，默认5000）
    page_num = 5000
#爬取图片
    while page_num <= 5010: #设置爬取页面：默认从5000-5010

        page_url = url + 'a/' + str(page_num) + '.html'
        print('正在加载以下URL，请稍后！')
        print(page_url)
        imgs = find_imgs(page_url)
        page_num += 1

        for each in imgs:
            filename = str(x) + '.' + each.split('.')[-1]
            x += 1
            with open(filename, 'wb') as f:
                img = url_open(each).content
                f.write(img)
    print('——————————图片下载完成———————————')

if __name__ == "__main__":
    url = 'http://www.meizitu.com/'
    download_imgs()

