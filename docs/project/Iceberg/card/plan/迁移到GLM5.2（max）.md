# 📋 **Balatro Love2D → Godot 4.7.1 迁移完整规划文档**

---

## **📌 项目概述**

### **目标**
将开源项目 **Balatro（从balatro.exe解压而来）** 从 **Love2D** 迁移到 **Godot 4.7.1**，保持原版的游戏机制、UI风格和视觉表现。

### **原项目技术栈**
- **引擎**: Love2D (Lua)
- **语言**: Lua 5.1
- **架构**: 单文件应用 + 模块化Lua脚本
- **资源**: 图集纹理、OGG音频、字体文件、GLSL着色器

### **目标技术栈**
- **引擎**: Godot 4.7.1
- **语言**: GDScript
- **架构**: 场景树 + Autoload + 事件总线
- **资源**: Godot 原生资源格式

---

---

# **🎯 AI 初始提示词（第一次对话必发）**

```
你现在是一个资深游戏客户端架构师与 Godot 工程师，负责将 Balatro Love2D 重制版迁移到 Godot 4.7.1。

## 核心要求
1. 代码风格: 高质量、可读性强、易维护
2. 注释要求: 全部中文注释
3. 架构原则: 组合优于继承、模块解耦、高内聚
4. 工程组织: 单代码文件挂载在根节点上生成全项目骨架

## 工作流程
1. 用户会上传当前阶段的代码
2. 你只需要分析代码并输出下一阶段的实现方案
3. 不要执行任何测试，只需要读取和分析代码
4. 每个阶段完成后，告诉用户需要上传什么代码

## 输出要求
- 结构清晰，结论明确
- 可直接进入实施阶段
- 结合实际代码分析
- 给出具体的代码实现方案

## 限制
- 不要空谈理论
- 不要执行 Godot 或 headless 测试
- 只分析代码，输出方案

现在开始阶段一的工作。
```

---

---

# **🏗️ 分阶段实施计划**

---

## **📅 阶段 0：准备阶段（用户完成）**

### **目标**
准备好所有必要的工具和资源

### **用户需要完成的任务**

| **任务** | **说明** | **验收标准** |
|----------|----------|--------------|
| 确认 Godot 4.7.1 可执行文件 | 在 `tool/Godot_v4.7.1-stable_linux.x86_64/` 目录下 | ✅ 文件存在且可执行 |
| 准备 balabala src 目录 | 包含完整的 Lua 源码 | ✅ 所有 .lua 文件可读 |
| 创建 Godot 项目目录 | `balabala-godot/` | ✅ 目录结构完整 |
| 准备资源文件 | `assets/` 目录下的字体、音效、纹理、着色器 | ✅ 所有资源文件可访问 |

### **用户需要上传的内容**
```
无（AI 直接读取仓库中的 balabala src 目录）
```

---

## **📅 阶段 1：架构搭建（AI 辅助 + 用户实施）**

### **目标**
建立完整的 Godot 工程结构和基础系统

### **AI 需要做的工作**

1. **分析原项目结构**
   - 读取 `balabala src/Balabala(从balabala.exe解压而来)/` 目录
   - 分析目录结构、模块划分、依赖关系
   - 输出项目分析报告

2. **设计 Godot 架构**
   - 设计目录结构
   - 设计场景树
   - 设计脚本分层
   - 设计 Autoload 单例
   - 设计事件总线

3. **生成 EditorScript**
   - 输出 `scripts/editor/project_generator.gd` 完整代码
   - 该脚本负责一次性生成：
     - 所有目录
     - 所有场景（.tscn）
     - 所有脚本模板（.gd）
     - 所有资源类（.gd）
     - 基础配置文件

4. **生成 project.godot**
   - 配置 Autoload
   - 配置渲染器
   - 配置输入映射

### **用户需要实施的任务**

| **任务** | **说明** | **AI 输出** | **验收标准** |
|----------|----------|-------------|--------------|
| 创建目录结构 | 按照 AI 设计创建所有目录 | 目录清单 | ✅ 所有目录存在 |
| 执行 EditorScript | 运行生成脚本 | EditorScript 代码 | ✅ 所有文件生成成功 |
| 配置 project.godot | 复制 AI 生成的配置 | project.godot 文件 | ✅ Godot 可正常打开项目 |
| 验证 Autoload | 检查 9 个 Autoload 是否加载 | Autoload 配置 | ✅ 所有 Autoload 正常加载 |

### **用户需要上传的内容**
```bash
# 上传以下文件/目录：
balabala-godot/
├── project.godot
├── scripts/
│   ├── autoload/
│   │   ├── game_manager.gd
│   │   ├── state_manager.gd
│   │   ├── event_bus.gd
│   │   ├── input_manager.gd
│   │   ├── audio_manager.gd
│   │   ├── save_manager.gd
│   │   ├── resource_loader.gd
│   │   ├── localization.gd
│   │   └── config.gd
│   ├── editor/
│   │   └── project_generator.gd
│   ├── core/
│   ├── systems/
│   ├── ui/
│   ├── utils/
│   └── resources/
│       ├── card_prototype.gd
│       ├── center_prototype.gd
│       ├── blind_prototype.gd
│       └── tag_prototype.gd
├── scenes/
│   ├── main.tscn
│   ├── splash/
│   ├── menu/
│   ├── game/
│   ├── ui/
│   └── _templates/
├── resources/
├── data/
└── tools/
```

### **阶段 1 完成标准**
- [ ] Godot 可以正常打开项目
- [ ] 所有 Autoload 脚本加载成功
- [ ] 可以在编辑器中看到生成的场景
- [ ] 事件总线可以正常工作
- [ ] 资源类可以创建和编辑

---

## **📅 阶段 2：资源迁移（AI 辅助 + 用户实施）**

### **目标**
将 Love2D 的资源文件迁移到 Godot 格式

### **AI 需要做的工作**

1. **分析原项目资源**
   - 读取 `assets/fonts/` 目录，设计字体导入方案
   - 读取 `assets/sounds/` 目录，设计音频导入方案
   - 读取 `assets/textures/` 目录，设计纹理导入方案
   - 读取 `assets/shaders/` 目录，设计着色器转换方案

2. **生成资源导入脚本**
   - 输出 `scripts/editor/resource_importer.gd`
   - 该脚本负责：
     - 批量导入字体文件
     - 批量导入音频文件
     - 批量导入纹理文件
     - 转换着色器代码

3. **设计纹理图集**
   - 分析原项目的图集结构
   - 设计 Godot 中的 AtlasTexture 配置
   - 生成图集导入配置

### **用户需要实施的任务**

| **任务** | **说明** | **验收标准** |
|----------|----------|--------------|
| 复制字体文件 | 从 `assets/fonts/` 复制到 `resources/fonts/` | ✅ 所有字体文件存在 |
| 复制音效文件 | 从 `assets/sounds/` 复制到 `resources/audio/sounds/` | ✅ 所有音效文件存在 |
| 复制纹理文件 | 从 `assets/textures/` 复制到 `resources/textures/` | ✅ 所有纹理文件存在 |
| 复制着色器文件 | 从 `assets/shaders/` 复制到 `resources/shaders/` | ✅ 所有着色器文件存在 |
| 执行资源导入 | 运行资源导入脚本 | ✅ 所有资源在 Godot 中可用 |

### **用户需要上传的内容**
```bash
# 上传资源目录结构：
balabala-godot/resources/
├── fonts/
│   ├── GoNotoCJKCore.ttf
│   ├── GoNotoCurrent-Bold.ttf
│   └── ...
├── audio/
│   ├── sounds/
│   │   ├── ambientFire1.ogg
│   │   ├── button.ogg
│   │   └── ...
│   └── music/
├── textures/
│   ├── 1x/
│   ├── 2x/
│   └── collabs/
└── shaders/
    ├── CRT.fs
    ├── background.fs
    └── ...
```

### **阶段 2 完成标准**
- [ ] 所有字体在 Godot 中可用
- [ ] 所有音效在 Godot 中可播放
- [ ] 所有纹理在 Godot 中可显示
- [ ] 所有着色器在 Godot 中可编辑

---

## **📅 阶段 3：数据迁移（AI 辅助 + 用户实施）**

### **目标**
将 Lua 中的数据结构迁移到 Godot 资源格式

### **AI 需要做的工作**

1. **分析原项目数据**
   - 读取 `game.lua` 中的 `P_CARDS`、`P_CENTERS`、`P_BLINDS`、`P_TAGS` 等原型数据
   - 读取 `globals.lua` 中的颜色、配置等常量
   - 读取 `localization/` 目录中的本地化文件

2. **生成数据转换脚本**
   - 输出 `scripts/editor/data_converter.gd`
   - 该脚本负责：
     - 将 Lua 表结构转换为 Godot Resource
     - 生成卡牌原型数据
     - 生成 Joker/Tarot/Planet 原型数据
     - 生成盲注原型数据
     - 生成标签原型数据
     - 生成挑战原型数据

3. **设计本地化系统**
   - 分析原项目的本地化机制
   - 设计 Godot 中的翻译文件格式
   - 生成本地化转换脚本

### **用户需要实施的任务**

| **任务** | **说明** | **验收标准** |
|----------|----------|--------------|
| 执行数据转换 | 运行数据转换脚本 | ✅ 所有 .res 文件生成 |
| 导入翻译文件 | 将 Lua 本地化转换为 Godot 翻译文件 | ✅ 所有语言可用 |
| 验证数据完整性 | 检查所有原型数据是否正确 | ✅ 数据与原版一致 |

### **用户需要上传的内容**
```bash
# 上传数据文件：
balabala-godot/resources/
├── cards/
│   └── prototypes.res
├── centers/
│   ├── jokers.res
│   ├── tarots.res
│   ├── planets.res
│   ├── spectral.res
│   └── vouchers.res
├── blinds/
│   └── prototypes.res
├── tags/
│   └── prototypes.res
└── localization/
    └── translations/
        ├── en-us.translation
        ├── zh_CN.translation
        └── ...

balabala-godot/data/
├── cards.json
├── centers.json
├── blinds.json
├── tags.json
└── challenges.json
```

### **阶段 3 完成标准**
- [ ] 所有卡牌原型数据可用
- [ ] 所有 Joker/Tarot/Planet 原型数据可用
- [ ] 所有盲注原型数据可用
- [ ] 所有标签原型数据可用
- [ ] 所有本地化文本可用

---

## **📅 阶段 4：核心系统实现（AI 辅助 + 用户实施）**

### **目标**
实现游戏核心逻辑系统

### **AI 需要做的工作（分4个子阶段）**

#### **子阶段 4.1：事件系统实现**

1. **分析原项目事件系统**
   - 读取 `engine/event.lua`，理解事件队列机制
   - 读取 `functions/common_events.lua`，理解公共事件

2. **实现 EventBus**
   - 完善 `scripts/autoload/event_bus.gd`
   - 实现事件发布/订阅
   - 实现延迟事件
   - 实现事件优先级

#### **子阶段 4.2：输入系统实现**

1. **分析原项目输入系统**
   - 读取 `engine/controller.lua`，理解输入处理
   - 读取 `main.lua` 中的输入回调

2. **实现 InputManager**
   - 完善 `scripts/autoload/input_manager.gd`
   - 实现键盘映射
   - 实现鼠标处理
   - 实现手柄支持
   - 实现输入事件分发

#### **子阶段 4.3：状态管理系统实现**

1. **分析原项目状态机**
   - 读取 `game.lua` 中的 `STATES` 和 `STAGES`
   - 理解状态切换逻辑

2. **实现 StateManager**
   - 完善 `scripts/autoload/state_manager.gd`
   - 实现状态注册
   - 实现状态切换
   - 实现状态回调

3. **实现 GameManager**
   - 完善 `scripts/autoload/game_manager.gd`
   - 实现场景切换
   - 实现游戏生命周期管理

#### **子阶段 4.4：卡牌系统实现**

1. **分析原项目卡牌系统**
   - 读取 `card.lua`，理解卡牌类
   - 读取 `cardarea.lua`，理解卡牌区域
   - 读取 `game.lua` 中的卡牌管理逻辑

2. **实现 Card 类**
   - 完善 `scripts/core/card.gd`
   - 实现卡牌属性
   - 实现卡牌行为
   - 实现卡牌渲染
   - 实现卡牌交互

3. **实现 CardArea 类**
   - 完善 `scripts/core/card_area.gd`
   - 实现卡牌容器
   - 实现卡牌排列
   - 实现卡牌管理

### **用户需要实施的任务**

| **任务** | **说明** | **验收标准** |
|----------|----------|--------------|
| 完善 EventBus | 按照 AI 方案实现 | ✅ 事件可以发射和接收 |
| 完善 InputManager | 按照 AI 方案实现 | ✅ 输入可以正常处理 |
| 完善 StateManager | 按照 AI 方案实现 | ✅ 状态可以正常切换 |
| 完善 GameManager | 按照 AI 方案实现 | ✅ 场景可以正常切换 |
| 完善 Card 类 | 按照 AI 方案实现 | ✅ 卡牌可以显示和交互 |
| 完善 CardArea 类 | 按照 AI 方案实现 | ✅ 卡牌区域可以管理卡牌 |

### **用户需要上传的内容**
```bash
# 上传完善后的核心脚本：
balabala-godot/scripts/autoload/
├── event_bus.gd
├── input_manager.gd
├── state_manager.gd
└── game_manager.gd

balabala-godot/scripts/core/
├── card.gd
└── card_area.gd
```

### **阶段 4 完成标准**
- [ ] 事件系统可以正常工作
- [ ] 输入系统可以正常处理
- [ ] 状态管理系统可以正常切换状态
- [ ] 卡牌可以正常显示和交互
- [ ] 卡牌区域可以正常管理卡牌

---

## **📅 阶段 5：UI 系统实现（AI 辅助 + 用户实施）**

### **目标**
实现完整的 UI 系统，还原原版视觉效果

### **AI 需要做的工作**

1. **分析原项目 UI 系统**
   - 读取 `engine/ui.lua`，理解 UI 基础类
   - 读取 `functions/UI_definitions.lua`，理解 UI 组件定义
   - 读取 `game.lua` 中的 UI 创建逻辑

2. **设计 Godot UI 系统**
   - 设计 UI 场景结构
   - 设计 UI 控制器
   - 设计 UI 主题

3. **生成 UI 实现方案**
   - 输出每个 UI 场景的实现方案
   - 输出每个 UI 控制器的代码框架

### **用户需要实施的任务**

| **任务** | **说明** | **验收标准** |
|----------|----------|--------------|
| 实现主菜单 UI | `scenes/menu/main_menu.tscn` | ✅ 主菜单可以正常显示和交互 |
| 实现 HUD | `scenes/ui/hud.tscn` | ✅ HUD 可以实时更新数据 |
| 实现商店 UI | `scenes/game/shop/shop.tscn` | ✅ 商店可以正常显示和交互 |
| 实现盲注选择 UI | `scenes/game/blind_select/blind_select.tscn` | ✅ 盲注选择可以正常工作 |
| 实现回合评分 UI | `scenes/game/round_eval/round_eval.tscn` | ✅ 回合评分可以正常显示 |
| 实现游戏结束 UI | `scenes/game/game_over/game_over.tscn` | ✅ 游戏结束界面可以正常显示 |
| 实现启动画面 | `scenes/splash/splash.tscn` | ✅ 启动画面可以正常播放 |

### **用户需要上传的内容**
```bash
# 上传完善后的 UI 场景和脚本：
balabala-godot/scenes/
├── splash/
│   └── splash.tscn
├── menu/
│   └── main_menu.tscn
├── game/
│   ├── shop/
│   │   └── shop.tscn
│   ├── blind_select/
│   │   └── blind_select.tscn
│   ├── round_eval/
│   │   └── round_eval.tscn
│   └── game_over/
│       └── game_over.tscn
└── ui/
    ├── hud.tscn
    └── button.tscn

balabala-godot/scripts/ui/
├── ui_manager.gd
├── hud_controller.gd
├── menu_controller.gd
├── shop_controller.gd
└── button.gd
```

### **阶段 5 完成标准**
- [ ] 所有 UI 场景可以正常打开
- [ ] UI 视觉效果与原版一致（90%+）
- [ ] UI 交互响应正常
- [ ] HUD 可以实时更新数据

---

## **📅 阶段 6：游戏逻辑实现（AI 辅助 + 用户实施）**

### **目标**
实现完整的游戏逻辑，包括回合流程、计分系统、商店系统等

### **AI 需要做的工作（分6个子阶段）**

#### **子阶段 6.1：回合系统**

1. **分析原项目回合逻辑**
   - 读取 `game.lua` 中的回合流程
   - 理解 `SELECTING_HAND`、`HAND_PLAYED`、`DRAW_TO_HAND` 等状态

2. **实现 RoundSystem**
   - 完善 `scripts/systems/round_system.gd`
   - 实现回合初始化
   - 实现回合更新
   - 实现回合结束

#### **子阶段 6.2：手牌系统**

1. **分析原项目手牌逻辑**
   - 读取 `game.lua` 中的手牌管理
   - 理解手牌类型判断

2. **实现 HandSystem**
   - 完善 `scripts/systems/hand_system.gd`
   - 实现手牌管理
   - 实现手牌类型判断（Pair, Two Pair, Three of a Kind, etc.）
   - 实现手牌评分

#### **子阶段 6.3：计分系统**

1. **分析原项目计分逻辑**
   - 读取 `game.lua` 中的计分逻辑
   - 理解筹码和倍率计算

2. **实现 ScoringSystem**
   - 完善 `scripts/systems/scoring_system.gd`
   - 实现筹码计算
   - 实现倍率计算
   - 实现奖励计算

#### **子阶段 6.4：商店系统**

1. **分析原项目商店逻辑**
   - 读取 `game.lua` 中的商店管理
   - 理解商店物品生成、购买、刷新逻辑

2. **实现 ShopSystem**
   - 完善 `scripts/systems/shop_system.gd`
   - 实现商店物品生成
   - 实现购买逻辑
   - 实现刷新逻辑

#### **子阶段 6.5：盲注系统**

1. **分析原项目盲注逻辑**
   - 读取 `blind.lua`，理解盲注类
   - 读取 `game.lua` 中的盲注管理

2. **实现 Blind 类**
   - 完善 `scripts/core/blind.gd`
   - 实现盲注属性
   - 实现盲注效果
   - 实现 Boss 战逻辑

#### **子阶段 6.6：Joker/Tarot/Planet 系统**

1. **分析原项目消耗品逻辑**
   - 读取 `game.lua` 中的消耗品管理
   - 理解各种消耗品的效果

2. **实现消耗品类**
   - 完善 `scripts/core/back.gd`
   - 完善 `scripts/core/tag.gd`
   - 完善 `scripts/core/challenge.gd`

### **用户需要实施的任务**

| **任务** | **说明** | **验收标准** |
|----------|----------|--------------|
| 完善 RoundSystem | 按照 AI 方案实现 | ✅ 回合可以正常开始和结束 |
| 完善 HandSystem | 按照 AI 方案实现 | ✅ 手牌类型可以正确判断 |
| 完善 ScoringSystem | 按照 AI 方案实现 | ✅ 计分可以正确计算 |
| 完善 ShopSystem | 按照 AI 方案实现 | ✅ 商店可以正常使用 |
| 完善 Blind 类 | 按照 AI 方案实现 | ✅ 盲注效果可以正常应用 |
| 完善消耗品类 | 按照 AI 方案实现 | ✅ 消耗品可以正常使用 |

### **用户需要上传的内容**
```bash
# 上传完善后的系统脚本：
balabala-godot/scripts/systems/
├── round_system.gd
├── hand_system.gd
├── scoring_system.gd
└── shop_system.gd

balabala-godot/scripts/core/
├── blind.gd
├── back.gd
├── tag.gd
└── challenge.gd
```

### **阶段 6 完成标准**
- [ ] 回合可以正常开始和结束
- [ ] 手牌类型可以正确判断
- [ ] 计分可以正确计算
- [ ] 商店可以正常使用
- [ ] 盲注效果可以正常应用
- [ ] 消耗品可以正常使用

---

## **📅 阶段 7：动画与特效（AI 辅助 + 用户实施）**

### **目标**
还原原版的动画效果和特效

### **AI 需要做的工作**

1. **分析原项目动画系统**
   - 读取 `engine/animatedsprite.lua`，理解动画精灵
   - 读取 `engine/particles.lua`，理解粒子系统
   - 读取 `game.lua` 中的动画逻辑

2. **设计 Godot 动画系统**
   - 设计卡牌动画
   - 设计 UI 动画
   - 设计粒子特效
   - 设计屏幕特效

3. **转换着色器代码**
   - 将 `.fs` 文件转换为 Godot 着色器语言
   - 生成着色器转换脚本

### **用户需要实施的任务**

| **任务** | **说明** | **验收标准** |
|----------|----------|--------------|
| 实现卡牌动画 | 翻转、出牌、弃牌等动画 | ✅ 卡牌动画流畅 |
| 实现 UI 动画 | 按钮、菜单等动画 | ✅ UI 动画与原版一致 |
| 实现粒子特效 | 粒子系统 | ✅ 粒子特效可以正常显示 |
| 实现屏幕特效 | CRT、背景等特效 | ✅ 屏幕特效可以正常应用 |
| 转换着色器 | 将所有 .fs 文件转换为 Godot 着色器 | ✅ 所有着色器可以正常工作 |

### **用户需要上传的内容**
```bash
# 上传着色器文件：
balabala-godot/resources/shaders/
├── crt.shader
├── background.shader
├── dissolve.shader
└── ...

# 上传动画系统：
balabala-godot/scripts/systems/
└── animation_system.gd
```

### **阶段 7 完成标准**
- [ ] 所有着色器可以正常工作
- [ ] 卡牌动画流畅自然
- [ ] UI 动画与原版一致
- [ ] 粒子特效可以正常显示
- [ ] 屏幕特效可以正常应用

---

## **📅 阶段 8：音频与存档（AI 辅助 + 用户实施）**

### **目标**
实现音频系统和存档系统

### **AI 需要做的工作**

1. **分析原项目音频系统**
   - 读取 `engine/sound_manager.lua`，理解音频管理
   - 理解多线程音频播放

2. **实现 AudioManager**
   - 完善 `scripts/autoload/audio_manager.gd`
   - 实现音效播放
   - 实现背景音乐
   - 实现音量控制
   - 实现音频池管理

3. **分析原项目存档系统**
   - 读取 `engine/save_manager.lua`，理解存档管理
   - 理解多线程存档读写

4. **实现 SaveManager**
   - 完善 `scripts/autoload/save_manager.gd`
   - 实现存档读写
   - 实现自动保存
   - 实现云存（可选）

### **用户需要实施的任务**

| **任务** | **说明** | **验收标准** |
|----------|----------|--------------|
| 完善 AudioManager | 按照 AI 方案实现 | ✅ 所有音效可以正常播放 |
| 完善 SaveManager | 按照 AI 方案实现 | ✅ 可以保存和加载游戏 |
| 配置音频文件 | 导入所有音效文件 | ✅ 所有音效在 Godot 中可用 |
| 测试存档功能 | 测试保存和加载 | ✅ 存档可以正常读写 |

### **用户需要上传的内容**
```bash
# 上传完善后的音频和存档脚本：
balabala-godot/scripts/autoload/
├── audio_manager.gd
└── save_manager.gd
```

### **阶段 8 完成标准**
- [ ] 所有音效可以正常播放
- [ ] 背景音乐可以正常播放
- [ ] 可以调节音量
- [ ] 可以保存和加载游戏
- [ ] 设置可以保存

---

## **📅 阶段 9：调试与验证（用户实施 + AI 辅助）**

### **目标**
全面测试和调试，确保游戏稳定运行

### **AI 需要做的工作**

1. **生成测试方案**
   - 输出单元测试方案
   - 输出集成测试方案
   - 输出 UI 测试方案
   - 输出性能测试方案

2. **分析测试结果**
   - 根据用户上传的测试结果，分析问题
   - 提供 bug 修复方案

3. **优化建议**
   - 提供性能优化建议
   - 提供代码重构建议

### **用户需要实施的任务**

| **任务** | **说明** | **验收标准** |
|----------|----------|--------------|
| 单元测试 | 测试各个模块 | ✅ 主要系统都有测试 |
| 集成测试 | 测试系统间协作 | ✅ 系统间可以正常协作 |
| UI 测试 | 测试 UI 交互 | ✅ UI 交互正常 |
| 卡牌测试 | 测试卡牌逻辑 | ✅ 卡牌逻辑正确 |
| 回合测试 | 测试回合流程 | ✅ 回合流程正常 |
| 商店测试 | 测试商店系统 | ✅ 商店功能正常 |
| 盲注测试 | 测试盲注系统 | ✅ 盲注效果正常 |
| Boss 测试 | 测试 Boss 战 | ✅ Boss 战正常 |
| 性能测试 | 测试性能 | ✅ FPS 稳定在 60+ |
| 兼容性测试 | 测试多平台 | ✅ 在目标平台正常运行 |

### **用户需要上传的内容**
```bash
# 上传测试报告：
- 单元测试结果
- 集成测试结果
- UI 测试结果
- 性能测试结果
- 兼容性测试结果
- 发现的 bug 列表
```

### **阶段 9 完成标准**
- [ ] 所有主要功能都可以正常使用
- [ ] 没有严重 bug
- [ ] FPS 稳定在 60+
- [ ] 在目标平台正常运行

---

---

# **📊 总体进度跟踪表**

| **阶段** | **状态** | **预计时间** | **实际时间** | **负责人** | **验收状态** |
|----------|----------|--------------|--------------|------------|--------------|
| 阶段 0：准备 | ✅ 完成 | 0.5 天 | - | 用户 | ✅ 通过 |
| 阶段 1：架构搭建 | ⏳ 进行中 | 1-2 天 | - | AI + 用户 | ❌ 待验收 |
| 阶段 2：资源迁移 | ⏳ 待开始 | 1-2 天 | - | AI + 用户 | ❌ 待开始 |
| 阶段 3：数据迁移 | ⏳ 待开始 | 2-3 天 | - | AI + 用户 | ❌ 待开始 |
| 阶段 4：核心系统 | ⏳ 待开始 | 5-7 天 | - | AI + 用户 | ❌ 待开始 |
| 阶段 5：UI 系统 | ⏳ 待开始 | 5-7 天 | - | AI + 用户 | ❌ 待开始 |
| 阶段 6：游戏逻辑 | ⏳ 待开始 | 7-10 天 | - | AI + 用户 | ❌ 待开始 |
| 阶段 7：动画特效 | ⏳ 待开始 | 3-5 天 | - | AI + 用户 | ❌ 待开始 |
| 阶段 8：音频存档 | ⏳ 待开始 | 2-3 天 | - | AI + 用户 | ❌ 待开始 |
| 阶段 9：调试验证 | ⏳ 待开始 | 3-5 天 | - | 用户 + AI | ❌ 待开始 |

---

---

# **🎯 最终交付物清单**

## **必交付项**

### **1. Godot 项目文件**
```bash
balabala-godot/
├── project.godot                    # 项目配置
├── .gitignore                      # Git 忽略
└── README.md                       # 项目说明
```

### **2. 场景文件**
```bash
balabala-godot/scenes/
├── main.tscn                       # 根场景
├── splash/
│   └── splash.tscn                 # 启动画面
├── menu/
│   ├── main_menu.tscn              # 主菜单
│   ├── settings.tscn               # 设置
│   └── deck_select.tscn            # 牌背选择
├── game/
│   ├── game_root.tscn              # 游戏根场景
│   ├── round/
│   │   └── round.tscn               # 回合场景
│   ├── shop/
│   │   └── shop.tscn                # 商店
│   ├── blind_select/
│   │   └── blind_select.tscn        # 盲注选择
│   ├── round_eval/
│   │   └── round_eval.tscn          # 回合评分
│   └── game_over/
│       └── game_over.tscn           # 游戏结束
└── ui/
    ├── hud.tscn                    # HUD
    ├── card.tscn                   # 卡牌预制体
    ├── joker.tscn                  # Joker 预制体
    └── button.tscn                  # 按钮预制体
```

### **3. 脚本文件**
```bash
balabala-godot/scripts/
├── autoload/                       # Autoload 脚本
│   ├── game_manager.gd
│   ├── state_manager.gd
│   ├── event_bus.gd
│   ├── input_manager.gd
│   ├── audio_manager.gd
│   ├── save_manager.gd
│   ├── resource_loader.gd
│   ├── localization.gd
│   └── config.gd
├── core/                           # 核心系统
│   ├── game.gd
│   ├── card.gd
│   ├── card_area.gd
│   ├── blind.gd
│   ├── back.gd
│   ├── tag.gd
│   └── challenge.gd
├── systems/                        # 子系统
│   ├── round_system.gd
│   ├── hand_system.gd
│   ├── scoring_system.gd
│   ├── shop_system.gd
│   ├── animation_system.gd
│   └── tutorial_system.gd
├── ui/                             # UI 脚本
│   ├── ui_manager.gd
│   ├── hud_controller.gd
│   ├── menu_controller.gd
│   ├── shop_controller.gd
│   └── button.gd
├── utils/                          # 工具函数
│   ├── constants.gd
│   ├── math_utils.gd
│   ├── table_utils.gd
│   ├── string_utils.gd
│   ├── color_utils.gd
│   └── easing.gd
├── resources/                      # 资源类
│   ├── card_prototype.gd
│   ├── center_prototype.gd
│   ├── blind_prototype.gd
│   └── tag_prototype.gd
└── editor/                         # 编辑器脚本
    └── project_generator.gd
```

### **4. 资源文件**
```bash
balabala-godot/resources/
├── fonts/                          # 字体
├── audio/                          # 音频
│   ├── sounds/                     # 音效
│   └── music/                      # 背景音乐
├── textures/                       # 纹理
│   ├── 1x/                         # 1x 纹理
│   ├── 2x/                         # 2x 纹理
│   └── collabs/                    # 合作纹理
├── shaders/                        # 着色器
├── localization/                   # 本地化
│   └── translations/               # 翻译文件
└── themes/                         # UI 主题
```

### **5. 数据文件**
```bash
balabala-godot/data/
├── cards.json                      # 卡牌数据
├── centers.json                    # Joker/Tarot 数据
├── blinds.json                     # 盲注数据
├── tags.json                       # 标签数据
└── challenges.json                 # 挑战数据
```

## **可选交付项**

1. **自动化测试脚本** - 用于自动化测试各个系统
2. **性能分析工具** - 用于分析游戏性能
3. **文档** - 开发文档、API 文档等
4. **Demo 版本** - 可玩的 Demo 版本

---

---

# **✅ 成功标准**

## **功能完整性**
- [ ] 所有原版 Balatro 功能都能在 Godot 中正常使用
- [ ] 卡牌系统完整
- [ ] Joker/Tarot/Planet 系统完整
- [ ] 盲注系统完整
- [ ] 商店系统完整
- [ ] 回合流程完整
- [ ] 计分系统完整

## **视觉还原度**
- [ ] UI 与原版一致度 ≥ 90%
- [ ] 卡牌显示与原版一致
- [ ] 动画效果与原版一致
- [ ] 特效与原版一致

## **性能达标**
- [ ] FPS 稳定在 60+
- [ ] 内存使用合理
- [ ] 加载时间合理

## **代码质量**
- [ ] 所有代码有中文注释
- [ ] 代码可读性强
- [ ] 代码易于维护
- [ ] 代码可扩展性好

## **兼容性**
- [ ] 在 Windows 上正常运行
- [ ] 在 Linux 上正常运行（可选）
- [ ] 在 macOS 上正常运行（可选）

---

---

# **📝 AI 与用户协作流程**

## **每个阶段的协作流程**

### **1. 用户上传代码**
用户按照阶段要求，上传对应的代码文件

### **2. AI 分析代码**
AI 读取用户上传的代码，分析：
- 代码结构
- 实现逻辑
- 存在的问题
- 优化空间

### **3. AI 输出方案**
AI 输出：
- 代码分析报告
- 问题列表
- 修复方案
- 优化建议
- 下一阶段实施方案

### **4. 用户实施**
用户根据 AI 的方案，实施代码修改

### **5. 循环迭代**
重复上述流程，直到阶段完成

---

## **AI 输出模板**

```
## 📋 代码分析报告

### 🔍 分析对象
- 文件：[文件路径]
- 行数：[行数]
- 复杂度：[复杂度评估]

### ✅ 优点
1. [优点1]
2. [优点2]
3. [优点3]

### ❌ 问题
1. **问题1**
   - 位置：[行数]
   - 类型：[错误/警告/建议]
   - 描述：[问题描述]
   - 影响：[影响说明]
   - 修复方案：[具体修复方案]

2. **问题2**
   - 位置：[行数]
   - 类型：[错误/警告/建议]
   - 描述：[问题描述]
   - 影响：[影响说明]
   - 修复方案：[具体修复方案]

### 🎯 优化建议
1. **建议1**
   - 当前实现：[当前实现]
   - 优化方案：[优化方案]
   - 预期收益：[收益说明]

2. **建议2**
   - 当前实现：[当前实现]
   - 优化方案：[优化方案]
   - 预期收益：[收益说明]

### 📝 下一步行动
1. [行动1]
2. [行动2]
3. [行动3]

### 🎯 验收标准
- [ ] 标准1
- [ ] 标准2
- [ ] 标准3
```

---

---

# **🏆 总结**

本文档提供了 **Balatro Love2D → Godot 4.7.1 迁移** 的完整规划方案，包括：

1. **AI 初始提示词** - 确保 AI 理解项目要求
2. **分阶段实施计划** - 9 个阶段，每个阶段有明确的目标、任务、产出
3. **协作流程** - AI 和用户如何高效协作
4. **交付物清单** - 每个阶段需要交付什么
5. **成功标准** - 如何判断项目成功

**建议用户：**
1. 按照阶段顺序逐步实施
2. 每个阶段完成后，上传对应的代码
3. AI 会分析代码并提供下一步方案
4. 保持代码的中文注释
5. 保持代码的可读性和可维护性

**预计总工期：30-45 天**

---

**🎉 现在可以开始阶段 1 的工作了！**