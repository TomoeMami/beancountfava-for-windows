# Beancount + Fava for Windows

[![Build](https://github.com/TomoeMami/beancountfava-for-windows/actions/workflows/build.yml/badge.svg)](https://github.com/TomoeMami/beancountfava-for-windows/actions/workflows/build.yml)

This repository contains GitHub Actions workflow that builds
the latest [Beancount](https://beancount.github.io/) and
[Fava](https://beancount.github.io/fava/) binaries for Windows (x64).

The workflow runs in a clean virtual machine maintained by GitHub
to minimize chances of including a virus or a malware. Because of
how the binaries are created, the [7z](https://www.7-zip.org/)
archives available from [Releases](https://github.com/milang/beancountfava-for-windows/releases)
page **must** (currently) be extracted to a hard-coded path
`C:\Users\Public\bin\fava`:

```text
C:\Users\Public\bin\fava
    ↪ (extracted directory "app" -- beancount + fava, self-contained via Python virtual environment)
    ↪ (extracted directory "python" -- private Python 3 instance used by "app")
```

The latest release is currently [Beancount 3.0.0](https://github.com/beancount/beancount/releases/tag/3.0.0)
and [Fava 1.30](https://github.com/beancount/fava/releases/tag/v1.30).

**[中文使用说明](https://github.com/TomoeMami/beancountfava-for-windows/blob/master/README_CN.md)**

# Installing the Compressed Package to the System

1. Download the `fava.zip` file packaged by GitHub Actions from either the [Release page](https://github.com/TomoeMami/beancountfava-for-windows/releases) or the [Artifacts page](https://github.com/TomoeMami/beancountfava-for-windows/actions).  

2. Press `Win + R`, type `cmd`, and press Enter to open the Command Prompt. Then, enter the following command:  

   ```cmd
   mkdir C:\Users\Public\bin\fava
   ```

   No response or the message "Subdirectory or file already exists" is normal.  

3. Press `Win + E` to open File Explorer, type `C:\Users\Public\bin\fava` in the address bar, and press Enter to navigate to this directory.  

4. Extract the downloaded `fava.zip` file until you see the `app` and `python` folders.  

   > **Note**: You may encounter an "Unsupported compression algorithm" error during extraction. This can be ignored.  

5. Copy these two folders into the previously opened `C:\Users\Public\bin\fava` directory.  

---

# Setting Up a Fava Shortcut

When using Fava, you need to specify a main file (see [Reference 1](https://www.starlg.cn/2019/07/13/Beancount-01/#%E5%A6%82%E4%BD%95%E5%9C%A8%E4%B8%BB%E6%96%87%E4%BB%B6%E4%B8%8B%E5%8C%85%E5%90%AB%E5%85%B6%E4%BB%96-bean-%E6%96%87%E4%BB%B6) or [byvoid's blog](https://byvoid.com/zhs/blog/beancount-bookkeeping-4/#%e5%a4%9a%e6%96%87%e4%bb%b6%e7%bb%84%e7%bb%87)). Here, we use `main.bean` as an example, but you can name it anything (e.g., `1.bean` or `114514.bean`).  

1. In the directory where your main beancount file (e.g., `main.bean`) is located, right-click, select **New > Text Document**, and open it.  

2. Copy the following content into the file:  

   ```cmd
   C:\Users\Public\bin\fava\app\Scripts\fava.exe main.bean
   ```

   > **Note**: If your main file is not named `main.bean`, replace `main.bean` with the full name of your main file (including the extension).  

3. Save and close the file, then rename it from `New Text Document.txt` to `fava.bat`.  

4. Double-click `fava.bat` to start Fava. A window will pop up with the following message:  

   ```
   Starting Fava on http://127.0.0.1:5000
   ```

5. Hold `Ctrl` and click the link in the window, or manually enter `http://127.0.0.1:5000` in your browser's address bar to access the Fava web interface.  

6. To stop Fava, simply close the pop-up window by clicking the ❌ button.  
