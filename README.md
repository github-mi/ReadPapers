# ReadPapers

Read deep learning papers based on different topics.

# todo

- language model fusion
- augmentation

# 公式说明
  
每个目录下都有两个同名文件，其中\*.tex.md是纯文本格式，\*.md是带图片的便于阅读格式。

使用[readme2tex](https://github.com/leegao/readme2tex) 将Latex公式转为svg图片：

```bash
python -m readme2tex --output README.tex.md README.md --nocdn
```

> 在使用readme2tex时将needs_inversion相关代码注释掉了。
