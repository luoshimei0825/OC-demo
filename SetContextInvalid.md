# Why do CGContextSetFillColorWithColor and CGContextFillRects both throw “invalid context 0x0” error?
[参考原文](https://stackoverflow.com/questions/39069209/why-do-cgcontextsetfillcolorwithcolor-and-cgcontextfillrects-both-throw-invalid)

原因是

```
  (Apparently, when you are calling this code, before you call UIGraphicsBeginImageContext(), 
  there is no current context. Therefore UIGraphicsGetCurrentContext() returns nil.)
```

正确调用顺序
```
  UIGraphicsBeginImageContext( rect.size )

  let context = UIGraphicsGetCurrentContext()
```
这样才可以获取争取的 context
