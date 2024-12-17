## windows 激活 Typora

- 记录时间: 2024/12/17

### 参考连接

- [参考github项目]([hazukieq/Yporaject: Ypora 最新版激发教程](https://github.com/hazukieq/Yporaject))
- [rust环境配置参考](https://blog.csdn.net/xinyingzai/article/details/135459640)



windows与linux的配置有点差异参考项目中的方法提到了windows的**原方法**,但是原方法是针对linux平台的,没有win平台的详细操作,所以记录一下windows平台的方法

## 步骤



### 1. 下载和安装 Typora

Typora 提供了 Windows 平台的安装包。可以按以下步骤进行安装：

- **下载 Typora 安装包**
   前往 [Typora 官网](https://typora.io/) 下载适用于 Windows 的安装包。
- **安装 Typora**
   双击下载的安装包（通常是 `.exe` 文件），按照安装向导完成安装。

### 2. 克隆 Yporaject 项目

在 Windows 上安装 Git 和配置项目：

- **安装 Git**
   前往 [Git 官网](https://git-scm.com/) 下载并安装 Git。

- **克隆 Yporaject 项目**
   打开命令提示符（或 PowerShell），然后运行以下命令来克隆项目：

  ```bash
  git clone https://github.com/hazukieq/Yporaject.git --depth=1
  ```

  如果您更愿意使用原始项目，可以分别克隆这两个仓库：

  ```bash
  git clone https://github.com/DiamondHunters/NodeInject --depth=1
  git clone https://github.com/DiamondHunters/NodeInject_Hook_example --depth=1
  ```

- **合并项目资源**
   进入 Yporaject 文件夹，并将原项目资源复制到该目录：

  ```bash
  mkdir Yporaject
  cp -r NodeInject/* Yporaject
  cp NodeInject_Hook_example/hook.js Yporaject/src
  cp -r NodeInject_Hook_example/license_gen Yporaject
  ```

### 3. 配置 Rust 编译环境

**ps**: 具体可以参照链接2,否则正常的配置环境较慢

Windows 上安装 Rust 编译环境：

- 安装 Rust

  下载并运行 Rust 安装程序：

  Rust 官方安装页

  ，选择 Windows 安装程序。运行以下命令检查安装是否成功：

  ```bash
  cargo -V
  ```

  如果返回 Rust 的版本信息，则说明安装成功。

### 4. 编译 Yporaject 项目

在 Yporaject 项目文件夹中，运行以下命令进行编译：

- **编译项目**
   打开命令提示符或 PowerShell，进入 Yporaject 文件夹：

  ```bash
  cd Yporaject
  cargo build
  ```

- **检查二进制文件**
   编译成功后，二进制文件应该生成在 `target/debug` 目录下。运行以下命令查看：

  ```bash
  dir target\debug
  ```

- **运行项目**
   运行以下命令启动程序：

  ```bash
  cargo run
  ```

  如果显示 `no node_modules.asar found`，表示程序未找到所需的 `node_modules.asar` 文件。确保 Typora 安装目录下有该文件，或者将该项目目录移至 Typora 安装目录。

### 5. 复制二进制文件到 Typora 安装目录

- **复制二进制文件**
   将编译生成的二进制文件 `node_inject` 复制到 Typora 安装目录下（默认路径为 `C:\Program Files\Typora` 或 `C:\Users\<YourUsername>\AppData\Local\Typora`）。

  ```bash
  copy target\debug\node_inject "C:\Program Files\Typora"
  ```

- **给予执行权限**
   在 Windows 上，权限通常不需要像 Linux 那样显式设置，但如果遇到问题，可以尝试以管理员权限运行命令提示符。

- **运行二进制文件**
   进入 Typora 安装目录并运行 `node_inject`：

  ```bash
  cd "C:\Program Files\Typora"
  node_inject
  ```

### 6. 获取许可证激活码

最后，进入 `license-gen` 文件夹并运行以下命令生成许可证激活码：

- **进入 `license-gen` 文件夹**

  ```bash
  cd license-gen
  ```

- **编译并运行代码**

  ```bash
  cargo build
  cargo run
  ```

- **获得许可证激活码**
   运行结果应该会输出一个类似于以下的许可证激活码：

  ```bash
  License for you: xxxxxx-xxxxxx-xxxxxx-xxxxxx
  ```

这样，您就完成了在 Windows 上的 Typora 和 Yporaject 的安装和配置。