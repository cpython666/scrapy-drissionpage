# scrapy-drissionpage
Scrapy的DrissionPage中间件

## 清单
首先应该实现一个最简单的请求功能
然后是睡眠，等待，超时时间，自动处理弹窗，执行脚本，等待元素，点击，
截屏，
代理，
隧道代理，

调用request中的DrissionPageRequest方法，而不是scrapy.Request方法
启用middlewares中的DrissionPageMiddleware中间件

静态页面可以在dom加载完成后返回页面
由js动态获取数据的页面需要等待网络完成之后返回页面

## 参考：
能否添加页面加载状态的判断？ #23：https://github.com/g1879/DrissionPage/issues/23

### 使用

```python
request_cls = DrissionPageRequest
custom_settings = {
    "DOWNLOADER_MIDDLEWARES": {
        "scrapy_drissionpage.middlewares.DrissionPageMiddleware": 560,
    }
}

yield self.request_cls(
    url=url,
    callback=self.parse,
    meta=meta,
    dont_filter=True,
)
```