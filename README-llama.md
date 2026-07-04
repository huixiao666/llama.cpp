# 🦙 llama.cpp Termux 便携版

**一键下载，解压即用！无需编译，开箱即用！**

## 📥 快速开始

```bash
# 1️⃣ 下载
wget https://github.com/huixiao666/llama.cpp/releases/download/latest/llama.cpp-termux-b9784-aarch64.tar.gz

# 2️⃣ 解压
tar -xzf llama.cpp-termux-b9784-aarch64.tar.gz
cd llama-pack

# 3️⃣ 检测环境
./setup.sh

# 4️⃣ 开始聊天（替换成你的模型路径）
./chat.sh ~/models/你的模型.gguf
```

## 📦 包含内容

| 组件 | 数量 |
|------|:----:|
| 🛠 命令行工具 (`llama-cli`, `llama-server`, `llama-bench` 等) | **38 个** |
| 📚 共享库 (含 Vulkan GPU 加速) | **21 个** |
| 🎮 Vulkan 驱动 | Freedreno + LVP 软渲染 |
| 📜 启动脚本 | `llama.sh` `chat.sh` `server.sh` `setup.sh` |

## 📱 兼容性

| 条件 | 状态 |
|------|:----:|
| **架构**: arm64-v8a (aarch64) | ✅ 任何新Android手机 |
| **系统**: 需要安装 Termux | ✅ 必须的 |
| **GPU 加速**: 骁龙 Adreno | 🚀 最佳性能 |
| **GPU 加速**: 其他芯片 (Mali等) | ✅ 自动检测系统驱动 |
| **无 GPU**: 任何设备 | ✅ 自动切换软渲染 |

## 🎯 使用示例

```bash
# 💬 交互式聊天（默认CPU+GPU加速）
./chat.sh ~/models/rwkv7-g1g-2.9b-Q8_0.gguf

# ⚡ 指定参数
./llama.sh cli -m ~/models/model.gguf -t 4 -ngl 99

# 🌐 启动API服务器（兼容OpenAI格式）
./llama.sh server -m ~/models/model.gguf -t 4 -ngl 99

# 📊 性能测试
./llama.sh bench -m ~/models/model.gguf -t 4 -ngl 99
```

### 关键参数说明
| 参数 | 说明 |
|------|------|
| `-t N` | CPU 线程数 |
| `-ngl N` | GPU 卸载层数 (`0`=纯CPU, `99`=全GPU) |
| `-n N` | 生成 token 数量 |
| `--prompt "你好"` | 直接提问 |

## 🏗 从源码构建

如果你想自己编译最新版：

```bash
pkg install cmake make ninja clang git vulkan-headers shaderc
git clone https://github.com/ggml-org/llama.cpp.git
cd llama.cpp && mkdir build && cd build
cmake .. -DGGML_VULKAN=ON -DCMAKE_BUILD_TYPE=Release
make -j$(nproc) llama-cli
```

## 🔗 相关链接

- [llama.cpp 官方](https://github.com/ggml-org/llama.cpp)
- [Termux](https://termux.dev/)
