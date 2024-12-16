# 使用vscode需要注意的事情
- 插件rust-analyzer: 在设置中
```json
    "terminal.integrated.defaultProfile.windows": "PowerShell",
    "rust-analyzer.semanticHighlighting.nonStandardTokens": false,
```

- 查看终端的环境变量是否有，如果没有，将`.cargo/bin`添加到环境变量