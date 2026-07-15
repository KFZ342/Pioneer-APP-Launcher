# 🚀 Pioneer APP Launcher

**iOS 上最自由的轻应用容器 / 极客工具集**

Pioneer APP Launcher 是一个轻量级的 iOS 应用容器，它允许你在 iPhone/iPad 上直接运行 Web 应用（HTML/CSS/JS），并通过 `JSBridge` 调用 iOS 原生系统权限。它完全不受 App Store 分发限制，支持从本地导入应用包，是一个"由用户掌控的轻应用平台"。

---

## ✨ 已实现功能（完整列表）

### 📦 核心容器
- ✅ 基于 `WKWebView` 的高性能 Web 应用运行环境  
- ✅ 完整的 `JSBridge` 双向通信机制（Web 应用可直接调用 iOS 原生能力）  
- ✅ 借鉴微信小程序思想的 `setData` 数据驱动视图机制  
- ✅ 内置 **5 个开箱即用的示例应用**（计算器、相机滤镜、音乐播放器、天气助手、待办清单）  

### 🔐 系统权限体系（目前已支持全部 iOS 系统权限）

| 权限 | 说明 |
|------|------|
| 相机 | 拍照、扫码、视频录制 |
| 麦克风 | 录音、语音输入 |
| 相册 | 读取、写入、保存图片 |
| 位置 | 使用时定位 / 始终定位 |
| 通知 | 推送通知 |
| 蓝牙 | BLE 设备连接 |
| 日历 | 读写日程事件 |
| 提醒事项 | 读写提醒列表 |
| 联系人 | 读取通讯录 |
| 语音识别 | 离线/在线语音转文字 |
| 本地网络 | 局域网设备发现（iOS 14+） |
| 健康数据 | 读取步数、心率、卡路里 |
| 运动传感器 | 加速度计、陀螺仪 |

> 所有权限均通过 `JSBridge` 暴露给 Web 应用，前端开发者无需学习 Swift 即可调用。

### 📂 应用管理
- ✅ 从本地导入 `.zip` 或文件夹格式的应用包  
- ✅ 自动解析 `manifest.json`（应用名称、版本、图标、入口文件等）  
- ✅ 应用列表展示（网格卡片，含 Emoji 图标 + 自定义背景色）  
- ✅ 应用删除、导出（打包为 `.zip`）  
- ✅ 应用收藏 / 取消收藏  
- ✅ 应用评分（0–5 星）  
- ✅ 使用统计（打开次数、最后使用时间、累计使用时长）  
- ✅ 应用数据持久化（`apps.json` 保存在沙盒中）

### 🎨 UI / 交互
- ✅ **UIKit + SwiftUI 混合界面**（应用卡片用 SwiftUI 绘制，整体用 UIKit 管理）  
- ✅ 应用列表网格布局（每行 2 个卡片）  
- ✅ 应用卡片显示：图标、名称、分类、评分星级、收藏标记  
- ✅ 搜索栏（实时过滤应用名称）  
- ✅ 分类筛选（全部 / 工具 / 娱乐 / 生活 / 学习）  
- ✅ 支持系统暗黑模式（自动跟随）  
- ✅ 长按应用卡片 → 弹出应用详情页（显示使用数据、评分滑块、导出/删除操作）  
- ✅ 双击导航栏标题 → 弹出调试面板（权限快速测试、沙盒路径查看、暗黑模式切换、清理缓存、使用统计等）  

### 🗣️ 语音控制
- ✅ 语音识别权限请求  
- ✅ 语音输入文字 → 自动搜索应用  
- ✅ 匹配到唯一应用时自动打开  

### 🧩 开发调试工具
- ✅ 内置调试面板（双击标题触发）  
- ✅ 一键请求所有系统权限（测试用）  
- ✅ 查看沙盒文件路径  
- ✅ 手动切换暗黑/亮色模式  
- ✅ 清理缓存  
- ✅ 显示应用使用统计（总应用数、总打开次数、收藏数、最常用应用）  
- ✅ 模拟位置（发送通知给天气应用）  
- ✅ 导出所有应用（打包成 ZIP）  
- ✅ 实时日志输出（调试面板内显示）  

### 🚀 无需越狱 / 无需上架
- ✅ 完全通过 **Xcode 编译 + 侧载** 即可安装使用  
- ✅ 支持 **TestFlight 内测分发**（最多 10000 人）  
- ✅ 支持 **AltStore / SideStore 等侧载工具**  
- ✅ 可在任意 iOS 设备上运行（iOS 14.0+）  
- ✅ 不上架 App Store，因此功能不受审核阉割  

---

## 📥 安装方式

### 方式一：TestFlight（推荐，无需电脑）
> 等待开放，后续将提供公开 TestFlight 链接。

### 方式二：手动编译（需要 Xcode）
```bash
git clone https://github.com/KFZ342/Pioneer-APP-Launcher.git
cd Pioneer-APP-Launcher
open Pioneer\ APP\ Launcher.xcodeproj
```
然后在 Xcode 中选择目标设备，点击 Run 即可。

### 方式三：侧载 IPA（需 AltStore / SideStore / Sideloadly）
> 后续将提供编译好的 `.ipa` 文件，可在 GitHub Releases 中下载。

---

## 📖 开发者文档

### `manifest.json` 规范

| 字段 | 类型 | 必填 | 说明 |
|------|------|------|------|
| `name` | String | ✅ | 应用名称 |
| `version` | String | ✅ | 版本号 |
| `entry` | String | ✅ | 入口文件（如 `index.html`） |
| `iconSymbol` | String | ❌ | SF Symbol 名称（如 `"star"`） |
| `iconColor` | String | ❌ | 十六进制颜色（如 `"#FF6B6B"`） |
| `category` | String | ❌ | 分类（工具/娱乐/生活/学习/其他） |

### `JSBridge` API 速查

Web 应用可通过 `window.NativeBridge` 调用以下方法：

```javascript
// 权限请求
NativeBridge.requestMicrophone(callback)
NativeBridge.requestCamera(callback)
NativeBridge.requestPhotoLibrary(callback)
NativeBridge.requestNotification(callback)
NativeBridge.requestLocation(callback)   // 使用时定位
NativeBridge.requestBluetooth(callback)
NativeBridge.requestCalendar(callback)
NativeBridge.requestReminders(callback)
NativeBridge.requestContacts(callback)
NativeBridge.requestSpeech(callback)
NativeBridge.requestLocalNetwork(callback)
NativeBridge.requestHealth(callback)
NativeBridge.requestMotion(callback)

// 获取所有权限状态
NativeBridge.getPermissionsStatus(callback)

// 回调示例
NativeBridge.requestCamera(function(result) {
    if (result.granted) {
        console.log('相机权限已授予');
    } else {
        console.log('相机权限被拒绝');
    }
});
```

### `setData` 数据驱动视图

在 Web 应用中定义 `render` 函数，然后调用 `setData` 更新数据，视图自动渲染：

```javascript
window.render = function(data) {
    document.getElementById('counter').textContent = data.counter;
};

// 更新数据 → 自动触发 render
window.setData({ counter: 10 });
```

---

## 🗺️ 未来计划（Roadmap）

- [ ] 内置应用商店（网页端 + 启动器内集成）  
- [ ] 应用自动更新机制  
- [ ] 更丰富的内置应用模板  
- [ ] 支持 PWA（渐进式 Web 应用）  
- [ ] 支持 WebAssembly  
- [ ] 更多极客功能（本地 Web 服务器、文件浏览器、应用快照等）  

---

## 📄 许可证

本项目采用 **MIT License**，你可以自由使用、修改、分发，但需保留版权声明。

---

## 🙋 反馈与贡献

- 提交 Issue：[GitHub Issues](https://github.com/KFZ342/Pioneer-APP-Launcher/issues)  
- 提交 Pull Request：欢迎任何改进或新增功能  
- 加入 QQ 群：待开放  

---

**好用记得点一个 Star，这是对我最大的支持！** ⭐
