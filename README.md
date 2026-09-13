# DeepVid Models

DeepVid Studio 的按需下载模型仓库。客户端程序本身不内置大模型；首次启用对应功能时，下载器会依据 [`manifest/stable.json`](manifest/stable.json) 下载、校验并安装模型。

## 当前稳定模型包

| 用途 | 模型包 | 支持语言 | 下载体积 |
| --- | --- | --- | --- |
| 本地音频/视频转写 | SenseVoiceSmall INT8 + Silero VAD | 中文、粤语、英语、日语、韩语 | 下载约 156 MB；安装后约 230 MB |

模型包用于 DeepVid Studio 的本地 ASR。它在用户电脑上运行，音频不会被发送到 DeepVid 的服务器。

## 发布约定

- 大型模型文件只作为 GitHub Release 附件发布，**不提交到 Git 历史**。
- 客户端只信任稳定清单中列出的 HTTPS 地址、文件大小与 SHA-256。
- 更新模型时创建新的不可变 Release tag；已发布的资产不覆盖。
- 下载器应先保存为 `.part`，完成 SHA-256 校验后再原子性地安装到应用数据目录的 `models/` 下。

## 目录

- `manifest/stable.json`：客户端读取的稳定通道清单。
- `LICENSES/THIRD_PARTY_NOTICES.md`：模型和运行时的上游来源及许可说明。

## 说明

本仓库目前只托管模型数据和机器可读清单；DeepVid Studio 的应用代码、模型驱动程序和更新逻辑位于主项目，二者独立版本化。
