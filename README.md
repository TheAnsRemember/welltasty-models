# WellTasty 模型包

WellTasty 本地版生成旋律所需要的 AI 模型权重，基于开源的 [ACE-Step 1.5](https://github.com/ace-step/ACE-Step-1.5)（MIT 许可证）。

**已经帮你瘦身过**：官方完整模型约 9.8 GB，其中约 3.5 GB 的语言模型（LM）WellTasty 用不到。这个包已经把那部分移除，只保留运行时真正需要的权重，体积约 **6.3 GB**。

## 下载

到右侧 **Releases** 页面，下载最新版里的 4 个分片：

```
welltasty-model-<日期>.tar.part-aa
welltasty-model-<日期>.tar.part-ab
welltasty-model-<日期>.tar.part-ac
welltasty-model-<日期>.tar.part-ad
```

外加一个 `SHA256SUMS.txt`（用来校验下载下来的文件有没有损坏）。

> GitHub 单个文件上限是 2 GB，所以 6.3 GB 的模型必须切成 4 片。下载后需要先合起来再用。

## 合并分片

**macOS / Linux**（终端里，cd 到下载目录）：

```bash
cat welltasty-model-*.tar.part-* > model.tar
shasum -a 256 -c SHA256SUMS.txt
```

**Windows**（命令提示符里，cd 到下载目录）：

```
copy /b welltasty-model-*.tar.part-* model.tar
```

第二条校验命令如果输出 `OK`，说明文件完整没损坏。

## 放到哪里

把合并出来的 `model.tar` 丢进 WellTasty 解压目录里的 `models/` 文件夹（没有就新建一个），然后双击启动脚本。脚本会自动识别、解压并安装到引擎目录，不会再去网上下载一遍。

如果你想手动放，解压目标是引擎的 `checkpoints/` 目录：

```bash
tar -xf model.tar -C <引擎目录>/checkpoints/
```

## 需要什么硬件

- 显存 4 GB 以上（NVIDIA 显卡体验最好）
- 内存 8 GB 以上
- 磁盘留出 6 GB 以上

## 许可与来源

模型权重来自 ACE-Step 1.5，遵循 **MIT 许可证**，版权归原作者所有。本仓库只是把它们瘦身整理后重新分发，方便 WellTasty 用户直接取用。

WellTasty 自身的程序代码不在这个仓库里。
