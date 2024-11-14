# 设计思路来源

[知乎文章](https://zhuanlan.zhihu.com/p/107201990)

# 参考代码

- [double_pinyin_abc](https://github.com/rime/rime-double-pinyin/blob/master/double_pinyin_abc.schema.yaml)

- [fime](https://gitee.com/zelde/fime)

# 实现思路

## 首先将三个字母转换成正常的双拼字母，然后利用已有的双拼输入法方案对词库进行转换

| Uv      | **A**bc | **D**ef |
|:-------:|:-------:|:-------:|
| **G**hi | **J**kl | **M**no |
| **P**qr | **S**tw | **X**yz |

这里加粗的字母并且大写的字母就是我每个案件上屏的字母

前两次的点击是为了选择对应字母所在的位置，**关键在于第三次点击，用于确定具体的组合**，比如输入`sxm`，最后的`m`处于第二行、第三列，那么`s`所在的`stw`要转换成`t`，`x`所在的`xyz`要转换成z，然后消除掉m，最后得到`tz`，这在智能abc输入法中对应的是`tizo`

# 词库的来源

- [雾凇拼音](https://github.com/iDvel/rime-ice/tree/main/cn_dicts)

tips：我将emoji做成dict.yaml加入到普通词库当中，如果不喜欢这种做法的可以在8105.dict.yaml当中注释掉cn_dict/emoji这一行



# 辅码来源

- [自然码](https://github.com/HowcanoeWang/rime-lua-aux-code)

- [墨奇码](https://github.com/gaboolic/moqima-tables)



# 碎碎语

最后的最后，不建议使用九宫格双拼+辅码的方案，目前还没有找到什么比较好的处理方式，用两个按键确定一个辅码的方式会导致按键过多，输入效率反而大大降低，并且导入自定义词库需要对词库的每个拼音后面添加","
