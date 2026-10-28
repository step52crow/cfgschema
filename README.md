# cfgschema

**统计配置的 schema 校验各部分的长度占比并标出异常。**

`cfgschema` —— 按段落统计配置的 schema 校验相关的长度分布，标出过长、过短与重复表达的部分

- 零依赖，Python 3.10+ 标准库即可运行
- 单文件，`cfgschema.py` 拷走就能用
- 不联网、不写文件

<!-- ipos:install -->
## 安装

零依赖，Python 3.10+ 即可：

```bash
pip install step52crow-cfgschema
```

装完直接用命令名调用：

```bash
cfgschema --help
```

也可以不用安装，直接把 `cfgschema.py` 拷走用——它只依赖标准库。

## 为什么需要它

区分「重复」与「必要冗余」——后者是刻意强调，不计入冗余

它遵守下面几条自己定的规矩：

1. **只报告能定位到具体位置的结论**，不做语义猜测。
2. **规则表公开**，每条命中都能对应到 配置的 schema 校验 领域的一条明示规则。
3. **输入为空或格式不对时明确报错**，不静默返回空结果。

## 用法

```bash
python cfgschema.py --file input.txt
python cfgschema.py --text "示例内容"
python cfgschema.py --file input.txt --json
```

加 `--json` 可以拿到机器可读的结果，便于接到流水线里。

## 已知局限

- 长度按字符与词统计，与具体 tokenizer 有偏差。
- 不判断长度是否「合理」，只报告分布。

## 跑测试

```bash
python test_cfgschema.py
```

测试用独立的断言与临时数据，不污染工作目录。

## 来源与参考

- Python 标准库文档：<https://docs.python.org/3/>
- GitHub 仓库：<https://github.com/step52crow/cfgschema>

---

## 关于作者

step52crow 做配置的 schema 校验相关的问题。这个工具先替你回答一个具体问题，再谈别的。

- 个人主页：<https://step52crow.github.io>
- 仓库：<https://github.com/step52crow/cfgschema>

## 许可

MIT，见 [LICENSE](LICENSE)。
