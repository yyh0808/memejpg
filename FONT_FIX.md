# 字体问题修复说明

## 🐛 问题描述

在初始配置中，网站字体显示过大，影响阅读体验。

## 🔍 问题原因

1. **错误的字体大小单位**: 在 `_config.next.yml` 中使用了 `px` 单位而不是 `em` 单位
2. **不正确的字体大小值**: 设置的数值过大（如 `size: 16` 被解释为 16em 而不是 16px）

## ✅ 解决方案

### 方案一：禁用自定义字体（推荐）

编辑 `_config.next.yml` 文件：

```yaml
# 字体设置
font:
  enable: false
```

这将使用Next主题的默认字体设置，通常是最稳定的选择。

### 方案二：正确配置自定义字体

如果需要自定义字体，使用正确的配置：

```yaml
# 字体设置
font:
  enable: true
  host: //fonts.googleapis.com
  global:
    external: true
    family: Lato
    size: 1          # 使用em单位，1em = 16px
  title:
    external: true
    family: Lato
    size: 1.625      # 约26px
  headings:
    external: true
    family: Lato
    size: 1.125      # 约18px
  posts:
    external: true
    family: Lato
    size: 1          # 约16px
  codes:
    external: true
    family: consolas
    size: 0.875      # 约14px
```

## 🔧 修复步骤

1. **编辑配置文件**
   ```bash
   # 编辑Next主题配置
   nano _config.next.yml
   ```

2. **修改字体设置**
   - 找到 `font:` 部分
   - 设置 `enable: false` 或使用正确的em单位

3. **清理和重建**
   ```bash
   npm run clean
   npm run build
   ```

4. **重启服务器**
   ```bash
   npm run server
   ```

5. **验证修复**
   - 访问 http://localhost:4000
   - 检查字体大小是否正常

## 📝 字体大小参考

### em单位换算
- `1em` = 16px（默认浏览器字体大小）
- `0.875em` = 14px
- `1.125em` = 18px
- `1.25em` = 20px
- `1.5em` = 24px

### 推荐设置
- **正文**: 1em (16px)
- **标题**: 1.5-2em (24-32px)
- **小字**: 0.875em (14px)
- **代码**: 0.875em (14px)

## 🚨 注意事项

1. **单位很重要**: 始终使用 `em` 或 `rem` 单位，不要使用 `px`
2. **测试必要**: 修改后务必测试不同设备和浏览器
3. **备份配置**: 修改前备份原始配置文件
4. **渐进调整**: 如果字体仍然不理想，逐步微调数值

## 🔄 回滚方案

如果修复后仍有问题，可以完全禁用自定义字体：

```yaml
font:
  enable: false
```

这将回到Next主题的默认字体设置。

## 📊 验证清单

- [ ] 字体大小适中，易于阅读
- [ ] 标题和正文有明显层次
- [ ] 移动端显示正常
- [ ] 代码块字体清晰
- [ ] 不同浏览器显示一致

## 🎯 最佳实践

1. **优先使用默认设置**: 除非有特殊需求，建议使用主题默认字体
2. **响应式考虑**: 确保字体在不同屏幕尺寸下都合适
3. **可读性优先**: 美观重要，但可读性更重要
4. **性能考虑**: 外部字体会影响加载速度

---

**修复完成后，字体应该显示正常，提供良好的阅读体验。** ✨
