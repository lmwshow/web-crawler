#coding=utf-8
import requests
import re
import cookielib


def getXSRF(data):                                                                #提取xsrf串
    cer = re.compile('name=\"_xsrf" value=\"(.*)\"')
    strlist = cer.findall(data)
    return strlist[0]



header = {
    'Connection': 'Keep-Alive',
    'Accept': '*/*',
    'Referer': 'http://www.zhihu.com/#signin',
    'Accept-Language': 'zh-CN',
    'Accept-Encoding': 'gzip, deflate',
    'User-Agent': 'Mozilla/5.0 (Windows NT 6.3; WOW64; Trident/7.0; rv:11.0) like Gecko',
    'Host': 'www.zhihu.com',
    'DNT': '1'
}

s = requests.session()          
url = 'http://www.zhihu.com/'

op = s.get(url,headers=header)
data = op.content

xsrf = getXSRF(data)
print xsrf                                                                  #提交的表单中的xsrf 需要我们从首页提取

url +='login/email'
id = '39*****39@qq.com'
password = '**********'
postDict = {
    '_xsrf' :xsrf,
    'password' : password,
    'remember_me' : 'true',
    'email' : id
}

op = s.post(url,data=postDict)
data = op.content
print(data)

url = 'https://www.zhihu.com/#signin'

op = s.get(url)
data = op.content
print data
