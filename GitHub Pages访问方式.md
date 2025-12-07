# GitHub Pages 访问方式（无需自定义域名）

## 一、GitHub Pages 提供的免费默认域名

即使**不配置自定义域名**，GitHub Pages 也会为你的仓库提供免费的默认访问地址。

### 访问地址格式

#### 方式 1：项目站点（Project Pages）
如果你的仓库名是 `myDocs`，GitHub 用户名是 `yourusername`：

**访问地址**：
```
https://yourusername.github.io/myDocs/
```

**特点**：
- 仓库名会出现在 URL 中
- 适用于项目文档、个人项目等

#### 方式 2：用户/组织站点（User/Organization Pages）
如果你创建了一个名为 `yourusername.github.io` 的特殊仓库：

**访问地址**：
```
https://yourusername.github.io/
```

**特点**：
- 更简洁的 URL
- 适用于个人主页、博客等

## 二、如何确定你的访问地址？

### 步骤 1：查看你的 GitHub 用户名
- 登录 GitHub
- 右上角头像 → 查看你的用户名

### 步骤 2：查看仓库名称
- 进入你的仓库页面
- 查看仓库名称（例如：`myDocs`）

### 步骤 3：确定访问地址

**如果是普通仓库**：
```
https://[你的用户名].github.io/[仓库名]/
```

**如果是特殊仓库 `[用户名].github.io`**：
```
https://[你的用户名].github.io/
```

## 三、部署 MkDocs 到 GitHub Pages

### 方法 1：使用 mkdocs gh-deploy（推荐）

```bash
# 安装 mkdocs-material（如果还没安装）
pip install mkdocs-material

# 部署到 GitHub Pages
mkdocs gh-deploy
```

这个命令会：
1. 自动构建网站
2. 创建或更新 `gh-pages` 分支
3. 推送到 GitHub
4. 自动启用 GitHub Pages

### 方法 2：手动部署

```bash
# 构建网站
mkdocs build

# 切换到 gh-pages 分支（如果不存在会自动创建）
git checkout -b gh-pages

# 复制构建文件
# Windows PowerShell
Copy-Item -Path site\* -Destination . -Recurse -Force

# 提交并推送
git add .
git commit -m "Deploy site"
git push origin gh-pages

# 切换回主分支
git checkout main
```

## 四、在 GitHub 中启用 Pages

### 步骤：

1. **进入仓库设置**
   - 打开你的 GitHub 仓库
   - 点击 **Settings**（设置）

2. **配置 Pages**
   - 左侧菜单找到 **Pages**
   - **Source**（源）选择：`Deploy from a branch`
   - **Branch**（分支）选择：`gh-pages`
   - **Folder**（文件夹）选择：`/ (root)`
   - 点击 **Save**（保存）

3. **等待部署**
   - 通常几分钟内完成
   - 页面会显示你的访问地址

## 五、访问你的网站

### 部署完成后：

1. **在 GitHub 仓库页面查看**
   - 进入仓库 → **Settings** → **Pages**
   - 会显示你的网站地址

2. **直接访问**
   - 在浏览器中输入你的 GitHub Pages 地址
   - 例如：`https://yourusername.github.io/myDocs/`

3. **验证**
   - 如果看到你的 MkDocs 网站，说明部署成功！

## 六、两种访问方式对比

| 特性 | GitHub 默认域名 | 自定义域名 |
|------|----------------|-----------|
| **费用** | 免费 | 需要购买域名（通常每年几十元） |
| **配置难度** | 简单，自动提供 | 需要配置 DNS |
| **URL 格式** | `username.github.io/repo` | `www.yourdomain.com` |
| **专业度** | 一般 | 更专业 |
| **SEO** | 包含 GitHub 标识 | 更利于 SEO |

## 七、实际示例

假设：
- GitHub 用户名：`zhangsan`
- 仓库名：`myDocs`

### 访问地址：
```
https://zhangsan.github.io/myDocs/
```

### 部署命令：
```bash
mkdocs gh-deploy
```

### 访问步骤：
1. 部署完成后，访问 `https://zhangsan.github.io/myDocs/`
2. 即可看到你的 MkDocs 文档网站

## 八、常见问题

### Q1: 部署后无法访问？
**A**: 
- 检查 GitHub Pages 是否已启用（Settings → Pages）
- 确认 `gh-pages` 分支已创建
- 等待几分钟让 GitHub 完成部署
- 检查 URL 是否正确（注意大小写）

### Q2: 404 错误？
**A**: 
- 确认 `gh-pages` 分支存在且有内容
- 检查 GitHub Pages 设置中的分支和文件夹配置
- 确认 `index.html` 文件在根目录

### Q3: 如何更新网站？
**A**: 
- 修改文档后，再次运行 `mkdocs gh-deploy`
- 或手动构建并推送到 `gh-pages` 分支

### Q4: 可以同时使用默认域名和自定义域名吗？
**A**: 
- 可以！配置自定义域名后，两个地址都可以访问
- 自定义域名会重定向到 GitHub 默认域名

## 九、总结

✅ **无需自定义域名也可以访问**：
- GitHub 自动提供 `username.github.io/repository` 格式的免费域名
- 部署后即可直接访问
- 完全免费，无需额外配置

✅ **配置自定义域名的好处**：
- 更专业的 URL
- 更好的品牌形象
- 更利于 SEO

**建议**：
- 初期可以使用 GitHub 默认域名快速部署和测试
- 后续如果需要，再配置自定义域名

