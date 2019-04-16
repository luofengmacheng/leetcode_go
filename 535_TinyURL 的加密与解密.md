## 535 TinyURL 的加密与解密

### 1 题目

TinyURL是一种URL简化服务，比如：当你输入一个URL`https://leetcode.com/problems/design-tinyurl`时，它将返回一个简化的URL `http://tinyurl.com/4e9iAk`。

要求：设计一个 TinyURL 的加密 encode 和解密 decode 的方法。你的加密和解密算法如何设计和运作是没有限制的，你只需要保证一个URL可以被加密成一个TinyURL，并且这个TinyURL可以用解密方法恢复成原本的URL。

### 2 解答

这个是网上常见的短URL，从一个长的URL经过编码可以变成一个比较短的URL，而且可以隐藏正常的URL中的信息，但是这里没有限制加解密算法，因此，只要是一个可逆的算法都可以，这里用base64算法。

``` python
import base64

class Codec:

    def encode(self, longUrl):

        return base64.b64encode(longUrl)
        

    def decode(self, shortUrl):

        return base64.b64decode(shortUrl)
```

但是，看网上的评论，说直接返回字符串也可以：

``` python
class Codec:

    def encode(self, longUrl):

        return longUrl
        

    def decode(self, shortUrl):

        return shortUrl
```

上面的例子可以通过，说明测试用例没有做一些校验，而且应该只要decode(encode(x))==x成立就行，不过，此题的目的应该是理解短url本身，而不是通过此题。