# web-crawler
# 解压gzip压缩数据 两种方法


1：

  import zlib
  
  import urllib2
  
  import urllib
  
  def ungzip(data):
  
      data = zlib.decompress(data,16+zlib.MAX_WBITS)
      
      return data
    
  request = urllib2.Request('http://xxxx.com')
  
  requset.add_hander('Accept-encoding','gzip')
  
  opener = urllib2.build_opener()
  
  f = opener.open(url)
  
  data = f.read()
  
  data = ungzip(data)
  
  print data
  
  
  
  
2:

  import urllib2
  
  import urllib
  
  import gzip
  
  import StringIO
  
  request = urllib2.Request('http://xxxx.com')
  
  requset.add_hander('Accept-encoding','gzip')
  
  opener = urllib2.build_opener()
  
  f = opener.open(url)
  
  compresssddata = f.read()
  
  compresssdstream = StringIO.StringIO(compresssddata)
  
  gzipper = gzip.GzipFile(fileobj=compresssdstream)
  
  print gzipper.read()
