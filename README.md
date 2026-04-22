# 自定义 MCP 服务（FastMCP + Python）

基于 **Model Context Protocol (MCP)** 开发的自定义工具服务，可被 Cherry Studio、Cursor 等 MCP 客户端调用，让大模型直接使用你开发的本地工具。

## 一、项目介绍

- 本项目是 MCP 服务端（Server）
- 支持标准 STDIO 通信，兼容所有主流 MCP 客户端
- 提供可扩展的工具函数，大模型可自动识别、自动调用
- 支持本地调试、日志查看、工具测试

## 二、已实现工具

1. hello—— 打招呼测试工具
2. calculator —— 四则运算计算器（+ - * /）
3. get_desktop_files —— 获取桌面文件列表

## 三、环境要求

- Python >= 3.11（推荐 3.13）
- Windows 
- 已安装：mcp、mcp[cli]

## 四、快速安装

```python
# 创建虚拟环境（可选）
conda create -n MCP python=3.13
conda activate MCP

# 安装依赖
pip install mcp
pip install mcp[cli]
```

## 五、启动服务

### 1. 直接启动（用于客户端连接）

```
python test.py
```

无输出 = 服务正常运行

### 2. 调试模式（网页面板调试，推荐）

```
mcp dev test.py
```

结果：![be44292eaa2b45eb80ddcbe12156736f](C:\Users\81955\AppData\Local\Temp\be44292eaa2b45eb80ddcbe12156736f.png)

## 六、对接 Cherry Studio（关键配置）

1. 打开 Cherry Studio → 设置 → MCP 服务器 → 添加服务器
2. 配置如下：
   - 名称：my-mcp（自定义）
   - 类型：标准输入 / 输出（STDIO）
   - 命令：你的 Python 绝对路径（用 where python 查询）
   - 参数：D:/learning/model/1/MCP/test.py（正斜杠路径）
3. 保存后**亮绿灯**即连接成功

## 七、使用示例

在 Cherry Studio 直接发送：

- 帮我用 calculator 计算 10 + 20

  ![3734b8747f844ab59e172a0e86ce8975](C:\Users\81955\AppData\Local\Temp\3734b8747f844ab59e172a0e86ce8975.png)

