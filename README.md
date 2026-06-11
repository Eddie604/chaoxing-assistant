# 学习通助手 - Chrome/Edge 浏览器扩展

自动刷学习通网课视频、AI自动答题和考试的浏览器扩展。

## 功能特性

### 📺 视频自动播放
- 自动检测并播放课程视频
- 支持 **1x ~ 16x** 可调节倍速
- 视频结束后自动切换到下一节
- 静音播放，不干扰其他操作
- 任务点自动完成

### 🤖 AI 自动答题
- 支持单选题、多选题、判断题、填空题、简答题
- 自动检测页面中的题目并提取
- 多AI模型并发请求，取最优答案
- 模拟真人打字速度填入答案
- 答题结果自动缓存（IndexedDB）

### 📝 考试模式
- 专门优化的考试答题流程
- 支持全部题目批量提取与批量作答
- 智能排序，先做客观题再做主观题

### 🔒 反检测保护
- 页面可见性伪装（防止切后台检测）
- 鼠标轨迹模拟（贝塞尔曲线）
- 随机操作延迟
- 键盘输入模拟
- 浏览器指纹清理

### 🎛️ 控制面板
- 可视化 Popup 控制面板
- 实时运行状态显示
- 统计数据（答题数、正确率等）
- API 密钥配置

## 支持的 AI 模型

| 模型 | API 提供商 | 配置方式 |
|------|-----------|---------|
| GPT-4o / GPT-4o-mini | OpenAI | 填入API Key |
| Claude 3.5 Sonnet | Anthropic | 填入API Key |
| DeepSeek V3 | DeepSeek | 填入API Key |
| 通义千问 | 阿里云 | 填入API Key |
| GLM-4 | 智谱AI | 填入API Key |
| 自定义接口 | 兼容OpenAI格式 | 填入Base URL + Key |

## 安装方法

### Chrome 浏览器
1. 打开 `chrome://extensions/`
2. 开启右上角「开发者模式」
3. 点击「加载已解压的扩展程序」
4. 选择 `chaoxing-assistant` 文件夹

### Edge 浏览器
1. 打开 `edge://extensions/`
2. 开启左下角「开发人员模式」
3. 点击「加载解压缩的扩展」
4. 选择 `chaoxing-assistant` 文件夹

## 使用方法

1. 打开学习通课程页面（`*.chaoxing.com` 或 `*.edu.cn`）
2. 点击浏览器工具栏中的扩展图标，打开控制面板
3. 在「设置」标签中配置 AI 模型的 API Key
4. 设置视频倍速（默认2x）
5. 点击「启动」开始自动刷课/答题

### 快捷键（Popup面板中）
- **视频模式**：自动播放视频 + 切集
- **答题模式**：检测并自动回答页面中的题目
- **考试模式**：进入考试页面后使用

## 项目结构

```
chaoxing-assistant/
├── manifest.json                    # 扩展清单
├── README.md
├── icons/                           # 图标
│   ├── icon16.png
│   ├── icon48.png
│   └── icon128.png
├── background/
│   └── service-worker.js            # Service Worker (后台)
├── content/
│   ├── content-script.js            # 主注入脚本
│   ├── content-style.css            # 页面注入样式
│   └── modules/
│       ├── video-handler.js         # 视频处理
│       ├── question-handler.js      # 题目处理
│       ├── answer-engine.js         # 答题引擎
│       ├── page-observer.js         # 页面监听
│       └── anti-detect.js           # 反检测
├── popup/
│   ├── popup.html                   # 控制面板
│   ├── popup.css
│   └── popup.js
└── utils/
    ├── api-clients.js               # AI API客户端
    ├── question-parser.js           # 题目解析
    ├── config.js                    # 配置管理
    ├── cache-db.js                  # 题库缓存 (IndexedDB)
    └── logger.js                    # 日志系统
```

## 技术栈

- **Manifest V3** 标准
- 纯原生 JavaScript（零依赖）
- Chrome Extension APIs
- IndexedDB 本地存储

## 注意事项

- 本扩展仅用于学习交流，请合理使用
- 使用前请确认已配置有效的 AI API Key
- API 调用可能产生费用，请注意控制用量
- 建议将视频倍速设置在合理范围内（推荐 1.5x ~ 3x）

## 版本

v1.0.0 - 初始版本

## 许可证

MIT License
