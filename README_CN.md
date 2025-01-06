# 使用说明

Beancount在Windows上安装，一直有一个绕不过去的[编译问题](https://beancount.github.io/docs/installing_beancount.html#install-compiler)，官方推荐的几种方式（MSVC编译器、WSL、Cygwin）都对非电脑专业用户很不友好（程序员也会被绕一下）。  

> [2025-01-06 周一 09:26] 更新：经测试，可以直接在Windows上通过pip安装fava和beancount，但是需要在[beancount的pypi文件界面](https://pypi.org/project/beancount/#files)查看发布的文件，注意「cp3xx」版本。
> 
> 如果你安装了最新的Python（此时为Python 3.13），则会发现用pip安装beancount时需要编译。
> 
> 2024年6月17日发布的beancount 3.0.0附带的whl文件最高由cp312（Python3.12）预编译而来，更新的Python版本需要安装MSVC等编译器。如果没有特殊版本需求，建议降级到3.12，直接在Microsoft Store中安装3.12即可。
> 
> 后续内容不再需要。如果有不懂安装Python的用户，也可以继续查看并使用。

幸好，我发现GitHub上早有人创建了Beancount+Fava的可执行打包exe脚本，但是疏于更新，上次发布已是三年前了。我fork了这个repo，并把打包的Beancount和Fava更新到了最新版本（Beancount 3.0.0 + Fava 1.30）。先将使用流程记录于下。  


## 安装压缩包到系统

1. 从 [Release 界面](https://github.com/TomoeMami/beancountfava-for-windows/releases) 或 [Action 界面](https://github.com/TomoeMami/beancountfava-for-windows/actions) 下载 GitHub Action 打包好的 `fava.zip` 文件。  

2. 按 `Win + R`，输入 `cmd` 并回车，打开命令提示符。然后输入以下命令：  

   ```cmd
   mkdir C:\Users\Public\bin\fava
   ```

   如果没有反应或提示「子目录或文件已存在」，这是正常的。  

3. 按 `Win + E` 打开文件资源管理器，在地址栏中输入 `C:\Users\Public\bin\fava` 并回车，进入该目录。  

4. 将下载的 `fava.zip` 文件解压，直到看到 `app` 和 `python` 两个文件夹。  

   > **注意**：解压时可能会遇到「不支持的压缩算法」错误，可以忽略。  

5. 将这两个文件夹复制到之前打开的 `C:\Users\Public\bin\fava` 目录中。  

---

## 设置启动 Fava 快捷方式

使用 Fava 时，需要指定一个主文件（参考 [Reference 1](https://www.starlg.cn/2019/07/13/Beancount-01/#%E5%A6%82%E4%BD%95%E5%9C%A8%E4%B8%BB%E6%96%87%E4%BB%B6%E4%B8%8B%E5%8C%85%E5%90%AB%E5%85%B6%E4%BB%96-bean-%E6%96%87%E4%BB%B6) 或 [byvoid 的博客](https://byvoid.com/zhs/blog/beancount-bookkeeping-4/#%e5%a4%9a%e6%96%87%e4%bb%b6%e7%bb%84%e7%bb%87)）。这里以 `main.bean` 为例，你也可以命名为 `1.bean` 或 `114514.bean`，都不影响。  

1. 在账本主文件（例如 `main.bean`）所在的目录中，右键点击空白处，选择 **新建 > 文本文档**，然后打开它。  

2. 将以下内容复制到文件中：  

   ```cmd
   C:\Users\Public\bin\fava\app\Scripts\fava.exe main.bean
   ```

   > **注意**：如果你的主文件不叫 `main.bean`，请将上面的 `main.bean` 替换为你的主文件全名（包括后缀）。  

3. 保存并关闭文件，然后将文件名改为 `fava.bat`。  

4. 双击 `fava.bat` 启动 Fava。会弹出一个窗口，显示以下信息：  

   ```
   Starting Fava on http://127.0.0.1:5000
   ```

5. 按住 `Ctrl` 并点击窗口中的链接，或者在浏览器地址栏中输入 `http://127.0.0.1:5000`，即可进入 Fava 的网页界面。  

6. 要关闭 Fava，只需点击弹出窗口右上角的 ❌ 按钮即可。  
