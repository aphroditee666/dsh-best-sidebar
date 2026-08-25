# @aphroditee666/dsh-best-sidebar

DeepSeek Harness（DSH）的 **VSCode 式右侧边栏插件**：文件树 / 编辑器 / 终端 / Git / 浏览器，按会话隔离。

本项目是 [`dsh-better-sidebar`](https://github.com/omdsh-dev/DSH-better-sidebar) 的 **fork 增强版**，在其基础上额外内置了三个实用补丁（已打进 `lib/` 构建产物，开箱即用）。

## 安装

```sh
dsh plugin --profile web add @aphroditee666/dsh-best-sidebar
```

安装后**重启 web profile** 生效：
```sh
dsh web
```

## 与上游的区别（内置补丁）

| 功能 | 说明 |
|------|------|
| **文件树静默自动刷新** | 每 2 秒轮询可见层级（根目录 + 已展开目录）做签名比对，**内容有变化才刷新**——不会像无脑轮询那样整棵清空重载导致界面跳动；浏览器页面在后台/手机锁屏时自动暂停 |
| **右键新建文件夹 / 新建文件** | 在文件树任意文件夹（或工作区根）上右键 → 「新建文件夹」「新建文件」，输入名字后创建并自动刷新（宿主新增 `fs.createDirectory` API） |
| **拖拽插入文件绝对路径** | 把文件树里的文件/文件夹**拖到对话输入框**（textarea），即在**光标位置**插入该文件的**绝对路径**（不带 `@`，选中区域会被替换，插入后光标停在路径末尾） |

其余能力与原版一致：文件预览/编辑（语法高亮）、终端（node-pty）、Git 面板、网页浏览器、多面板分栏、侧边聊天等。

## 注意事项

- 本包**源码（`src/`）已内置上述补丁**，可正常执行 `pnpm install && pnpm build` 重建 `lib/`（产物会自动使用新包名与补丁），不会丢失功能。
- `dsh plugin remove @aphroditee666/dsh-best-sidebar` 可卸载。
- 升级 DSH 需要配套升级本插件（DSH 仍为预发布阶段，RC 间客户端接口可能变化）。

## 许可

MIT（上游 dsh-better-sidebar 亦为 MIT）。