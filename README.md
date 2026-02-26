# Claude Settings Profile Manager

管理 `~/.claude/settings.json` 的多个配置文件。

## 快速开始

```bash
# 直接使用
~/.claude/claude-profile <命令>

# 或者添加到 PATH（推荐）
echo 'export PATH="$HOME/.claude:$PATH"' >> ~/.bashrc
source ~/.bashrc
claude-profile <命令>
```

## 命令说明

| 命令 | 说明 | 示例 |
|------|------|------|
| `list` / `ls` | 列出所有配置和备份 | `claude-profile list` |
| `save` / `s <名称>` | 保存当前配置 | `claude-profile save work` |
| `load` / `l <名称>` | 加载指定配置 | `claude-profile load work` |
| `switch` / `sw` | **交互式切换配置** | `claude-profile switch` |
| `backup` / `b [名称]` | 备份当前配置 | `claude-profile backup` |
| `restore` / `r <名称>` | 恢复备份 | `claude-profile restore auto_20250226_120000` |
| `show <名称>` | 显示配置内容 | `claude-profile show work` |
| `edit` / `e <名称>` | 编辑配置文件 | `claude-profile edit` |
| `diff <配置1> [配置2]` | 比较配置差异 | `claude-profile diff work current` |
| `delete` / `rm <名称>` | 删除配置 | `claude-profile delete old` |

## 目录结构

```
~/.claude/
├── settings.json       # 当前使用的配置
├── profiles/           # 命名配置存储
│   ├── work.json
│   ├── home.json
│   └── ...
└── backups/            # 自动备份存储
    ├── before_load_20250226_120000.json
    └── ...
```

## 使用场景

### 1. 快速切换配置（推荐）
```bash
# 交互式选择并切换配置
claude-profile switch
# 使用 ↑↓ 键选择，Enter 确认，支持模糊搜索（如果安装了 fzf）
```

### 2. 工作与家庭配置分离
```bash
# 保存工作配置
claude-profile save work

# 保存家庭配置
claude-profile save home

# 切换配置
claude-profile switch  # 交互式选择
# 或
claude-profile load work  # 直接指定名称
```

### 2. 测试新配置
```bash
# 先备份
claude-profile backup before-test

# 修改 settings.json 测试...

# 不满意直接恢复
claude-profile restore before-test_YYYYMMDD_HHMMSS
```

### 3. 查看配置差异
```bash
claude-profile diff work 当前
```
