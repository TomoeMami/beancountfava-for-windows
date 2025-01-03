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
