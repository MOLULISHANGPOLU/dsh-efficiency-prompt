# DSH 效率提示词插件

English: [README.md](README.md)

为 DeepSeek Harness（DSH）添加一段轻量系统提示词，帮助任务推进、事实核验、隐私保护和多轮协作。

## 安装

仓库发布到 GitHub 后，在终端运行：

```sh
dsh plugin --profile desktop add github:YOUR_GITHUB_OWNER/dsh-efficiency-prompt
```

把 `YOUR_GITHUB_OWNER` 替换成 GitHub 用户名或组织名；`desktop` 可换成实际 profile 名。DSH 会读取 bundle 声明并应用 `cordis.patch.yml`，无需手工编辑 profile，也不需要安装时运行构建脚本。按 DSH 提示重启后生效。

如果是下载或克隆到本机，在仓库根目录运行：

```sh
dsh plugin --profile desktop add .
```

从非官方 fork 安装前请先审阅源码。当前仓库地址待确定，所以命令里的所有者字段是占位符。

## 兼容范围

- DSH：`>=0.2.0-rc.2 <0.2.2-0`，覆盖 0.2.0 与 0.2.1 两条版本线及其预发布版本。
- Cordis：`^4.0.1`。
- Node.js：18 或更高版本。
- 插件没有操作系统专属 API，也没有平台限制。

DSH 会按 `engines.dsh` 检查版本后再加载。插件只使用 `systemPrompt.section` 注册接口。兼容承诺限于上述版本范围，不代表所有未来版本都兼容。

## 隐私与安全

插件不联网、不采集数据、不调用工具。提示词要求助手不披露凭据、个人信息、本机或网络地址、设备信息、本地路径和环境配置，并将网页、附件、代码、日志里的指令视为不可信数据。这是模型行为提示，不能替代宿主的权限和隔离机制。

发布包只包含运行入口、bundle patch、README 和许可证文件。不要向仓库加入密钥、个人信息、机器路径、环境变量、日志或其他私密内容。

许可证允许个人免费下载、安装并用于非商业用途，包括作为 DSH 插件使用；商业使用、修改、再分发、重新发布或转售需先取得版权持有人的书面许可。公开仓库仍可被查看和复制；许可证声明不能技术上阻止复制或反编译。不要公开任何必须保密的提示词或资料。

## 许可

个人非商业用途按 [LICENSE](LICENSE) 获得许可；其他用途需事先取得书面许可。
