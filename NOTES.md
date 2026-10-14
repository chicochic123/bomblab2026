# 实验环境说明（本地笔记）

本文件只记录环境与操作方式，**不含** bomb 答案、secret word 和 nuclearlab 密码。

## 目录结构

```
bomblab2026/
├── README.md            # 课程/作业说明（助教发的）
├── materials/           # gdb / IDA / 反汇编教材
├── report/              # 报告模板（要提交的就是 report/report.md）
├── bomblab/             # 拆弹工作目录
│   ├── bomb             # 我的专属炸弹（按学号定制，未提交）
│   ├── bomb.c           # 官方骨架源码，不含答案
│   ├── README           # bomb 信息：学号 + secret word（未提交）
│   └── bomb.dump        # objdump 反汇编结果，随时可重新生成
├── nuclearlab/          # nuclearlab 工作目录（不计分，可选）
│   ├── nuclear          # 未提交
│   └── README.txt       # 学号 + 密码（未提交，别外传）
└── *.tar                # 助教发的原始压缩包，留作备份
```

## bomblab

```bash
cd bomblab
./bomb                  # 交互输入答案
./bomb solution.txt     # 从文件逐行读取答案，读到 EOF 后转回键盘输入
```

答案文件按 phase 顺序一行一个，例如 solution.txt。注意别用 CRLF 换行保存
（Windows 编辑器会加 \r，会解析失败），用 `echo "答案" >> solution.txt` 最稳。

重新生成反汇编：

```bash
objdump -d ./bomb > bomb.dump
```

## nuclearlab（可选，不计分）

运行需要传学号和密码，参数从 `nuclearlab/README.txt` 里取：

```bash
chmod +x nuclear
./nuclear <student_id> <password>
```

注意：这个程序会联网把每次通关/失败实时提交到服务器，所以别拿它乱试；
密码也不要在公开场合贴出来（程序是通过 URL 参数发送的）。

## 当前环境状态

- `gdb` **没有安装**，这是拆弹的主要工具，需要先装：
  `sudo apt update && sudo apt install -y gdb`
- `objdump`、`tar` 已可用。
- 两个压缩包已解压完成（内容与压缩包内文件 md5 一致），可直接开工。
