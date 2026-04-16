# 赛罗奥特曼英语大作战 - 项目文档

## 1. 项目概述

**赛罗奥特曼英语大作战**是一个面向儿童的英语学习游戏，通过游戏化的方式激发学习兴趣，提高英语学习效果。

- **核心功能**：英语单词学习、战斗游戏模式、口语练习、错题本、怪兽养成、成就系统
- **技术栈**：纯HTML5 + CSS3 + JavaScript
- **目标用户**：儿童英语学习者
- **游戏特色**：奥特曼主题、怪兽战斗、角色扮演、积分系统

## 2. 项目架构

### 2.1 整体结构

该项目采用单文件应用架构，所有代码集中在一个`index.html`文件中，包含HTML结构、CSS样式和JavaScript逻辑。

```
index.html
├── HTML结构：游戏界面和UI组件
├── CSS样式：游戏视觉效果和动画
└── JavaScript逻辑：游戏核心功能实现
```

### 2.2 核心模块

| 模块 | 主要职责 | 文件位置 |
|------|---------|----------|
| 游戏核心 | 游戏逻辑、战斗系统、关卡管理 | [index.html](file:///workspace/index.html) |
| 语音系统 | 语音合成、语音识别 | [index.html](file:///workspace/index.html) |
| 数据管理 | 本地存储、数据导入/导出 | [index.html](file:///workspace/index.html) |
| UI管理 | 界面渲染、动画效果 | [index.html](file:///workspace/index.html) |
| 怪兽系统 | 怪兽数据、养成系统 | [index.html](file:///workspace/index.html) |
| 成就系统 | 成就解锁、进度追踪 | [index.html](file:///workspace/index.html) |
| 每日任务 | 任务管理、奖励系统 | [index.html](file:///workspace/index.html) |

## 3. 核心功能

### 3.1 英语学习系统

**词汇库**：基于Kids Box教材，分为3个级别，每个级别包含12个单元的单词和句子。

```javascript
const LEVEL_DATA = {
    1: { /* Level 1 词汇和句子 */ },
    2: { /* Level 2 词汇和句子 */ },
    3: { /* Level 3 词汇和句子 */ }
};
```

**学习模式**：
- 选择级别和单元
- 战斗模式学习（通过答题击败怪兽）
- 口语练习模式
- 错题本复习
- 快速闯关模式

### 3.2 战斗系统

**战斗机制**：
- 每关面对一个怪兽
- 通过答题减少怪兽生命值
- 答错会减少玩家生命值
- 连击系统：连续答对题目获得额外奖励

**关卡配置**：
```javascript
const STAGE_CONFIG = {
    quick: [/* 快速模式关卡配置 */],
    full: [/* 完整模式关卡配置 */]
};
```

### 3.3 语音系统

**语音合成**：使用Web Speech API实现单词发音
**语音识别**：支持口语练习和语音答题

```javascript
function speakCurrentWord() {
    // 语音合成实现
}

function toggleRecordClick() {
    // 语音识别实现
}
```

### 3.4 怪兽系统

**怪兽数据**：包含120+个奥特曼系列怪兽

```javascript
const ALL_MONSTERS = [
    {id:1,emoji:"👾",name:"巴尔坦星人",desc:"蝉型宇宙人，初代奥特曼宿敌"},
    // 更多怪兽...
];
```

**怪兽养成**：
- 解锁新怪兽
- 怪兽技能系统
- 怪兽进化

### 3.5 成就系统

**成就列表**：
```javascript
const ACHIEVEMENTS = {
    first_blood: {name:"初战告捷",desc:"完成第一场战斗",icon:"⚔️",condition:function(){return monstersDef>=10;}},
    // 更多成就...
};
```

### 3.6 每日任务

**任务类型**：
- 每日签到
- 答题挑战
- 口语练习
- 每日挑战

```javascript
const DAILY_CHALLENGES = [
    { id: 'combo', name: '🔥 连击挑战', desc: '单场达到5连击', check: function(){ return comboData.maxCombo >= 5; }, reward: 50, rewardType: 'energy' },
    // 更多挑战...
];
```

## 4. 关键类与函数

### 4.1 核心游戏函数

| 函数名 | 功能描述 | 参数 | 返回值 | 位置 |
|--------|---------|------|--------|------|
| `init()` | 游戏初始化 | 无 | 无 | [index.html](file:///workspace/index.html#L1430) |
| `startBattle()` | 开始战斗 | 无 | 无 | [index.html](file:///workspace/index.html) |
| `nextQuestion()` | 加载下一题 | 无 | 无 | [index.html](file:///workspace/index.html) |
| `checkAnswer()` | 检查答案 | option: 选项索引 | 无 | [index.html](file:///workspace/index.html) |
| `updateUI()` | 更新游戏UI | 无 | 无 | [index.html](file:///workspace/index.html) |

### 4.2 语音系统函数

| 函数名 | 功能描述 | 参数 | 返回值 | 位置 |
|--------|---------|------|--------|------|
| `preloadVoices()` | 预加载语音引擎 | 无 | 无 | [index.html](file:///workspace/index.html#L1374) |
| `warmupVoiceEngine()` | 预热语音引擎 | 无 | 无 | [index.html](file:///workspace/index.html#L1416) |
| `speakCurrentWord()` | 播放当前单词发音 | 无 | 无 | [index.html](file:///workspace/index.html) |
| `toggleRecordClick()` | 切换录音状态 | 无 | 无 | [index.html](file:///workspace/index.html) |

### 4.3 数据管理函数

| 函数名 | 功能描述 | 参数 | 返回值 | 位置 |
|--------|---------|------|--------|------|
| `saveProgress()` | 保存游戏进度 | 无 | 无 | [index.html](file:///workspace/index.html) |
| `loadProgress()` | 加载游戏进度 | 无 | 无 | [index.html](file:///workspace/index.html) |
| `exportProgress()` | 导出游戏数据 | 无 | 无 | [index.html](file:///workspace/index.html) |
| `importProgress()` | 导入游戏数据 | event: 文件选择事件 | 无 | [index.html](file:///workspace/index.html) |
| `exportQuestionBank()` | 导出题库 | 无 | 无 | [index.html](file:///workspace/index.html) |
| `importQuestionBank()` | 导入题库 | event: 文件选择事件 | 无 | [index.html](file:///workspace/index.html) |

### 4.4 怪兽系统函数

| 函数名 | 功能描述 | 参数 | 返回值 | 位置 |
|--------|---------|------|--------|------|
| `selectBattleMonsters()` | 选择战斗怪兽 | 无 | 怪兽数组 | [index.html](file:///workspace/index.html#L1277) |
| `unlockNewMonster()` | 解锁新怪兽 | count: 解锁数量 | 解锁的怪兽数组 | [index.html](file:///workspace/index.html#L1290) |
| `calculateUnlockCount()` | 计算解锁怪兽数量 | 无 | 解锁数量 | [index.html](file:///workspace/index.html#L1317) |
| `checkSpecialUnlock()` | 检查特殊解锁条件 | 无 | 特殊解锁的怪兽数组 | [index.html](file:///workspace/index.html#L1335) |

### 4.5 每日任务函数

| 函数名 | 功能描述 | 参数 | 返回值 | 位置 |
|--------|---------|------|--------|------|
| `checkDailyTaskReset()` | 检查每日任务重置 | 无 | 无 | [index.html](file:///workspace/index.html#L1457) |
| `checkLoginReward()` | 检查登录奖励 | 无 | 无 | [index.html](file:///workspace/index.html#L1480) |
| `showLoginReward()` | 显示登录奖励弹窗 | 无 | 无 | [index.html](file:///workspace/index.html#L1490) |
| `claimLoginReward()` | 领取登录奖励 | 无 | 无 | [index.html](file:///workspace/index.html#L1507) |
| `updateDailyTaskUI()` | 更新每日任务UI | 无 | 无 | [index.html](file:///workspace/index.html#L1524) |

## 5. 数据结构

### 5.1 词汇库数据

```javascript
const LEVEL_DATA = {
    1: { // Level 1
        1: { // 单元1
            words: ["hello","你好"], // 单词数组
            sentences: ["Hello!","你好！"] // 句子数组
        },
        // 更多单元...
    },
    // 更多级别...
};
```

### 5.2 怪兽数据

```javascript
const ALL_MONSTERS = [
    {id:1,emoji:"👾",name:"巴尔坦星人",desc:"蝉型宇宙人，初代奥特曼宿敌"},
    // 更多怪兽...
];
```

### 5.3 对话场景数据

```javascript
const DIALOGUE_SCENES = [
    {scene:"打招呼",question:"Hello! How are you?",options:["I'm fine, thanks!","Goodbye!","What's your name?"],correct:0},
    // 更多对话场景...
];
```

### 5.4 游戏状态数据

| 变量名 | 类型 | 描述 | 位置 |
|--------|------|------|------|
| `score` | 数值 | 玩家能量值 | [index.html](file:///workspace/index.html#L988) |
| `level` | 数值 | 玩家等级 | [index.html](file:///workspace/index.html#L1007) |
| `totalStars` | 数值 | 收集的星星数量 | [index.html](file:///workspace/index.html#L1008) |
| `currentLevel` | 数值 | 当前选择的词汇级别 | [index.html](file:///workspace/index.html#L728) |
| `battleMonsters` | 数组 | 战斗怪兽列表 | [index.html](file:///workspace/index.html#L985) |
| `unlockedMonsterIds` | 数组 | 已解锁的怪兽ID | [index.html](file:///workspace/index.html#L986) |
| `wrongBook` | 数组 | 错题本 | [index.html](file:///workspace/index.html#L1151) |
| `studyStats` | 对象 | 学习统计数据 | [index.html](file:///workspace/index.html#L1229) |
| `dailyTasks` | 对象 | 每日任务数据 | [index.html](file:///workspace/index.html#L1257) |

## 6. 依赖关系

| 依赖 | 类型 | 用途 | 位置 |
|------|------|------|------|
| Web Speech API | 浏览器API | 语音合成和识别 | [index.html](file:///workspace/index.html) |
| localStorage | 浏览器API | 本地数据存储 | [index.html](file:///workspace/index.html) |
| CSS3 Animations | 浏览器特性 | 动画效果 | [index.html](file:///workspace/index.html) |
| CSS3 Flexbox/Grid | 浏览器特性 | 布局 | [index.html](file:///workspace/index.html) |

## 7. 项目运行方式

### 7.1 本地运行

1. 直接在浏览器中打开 `index.html` 文件
2. 无需安装任何依赖
3. 游戏会自动初始化并加载上次保存的进度

### 7.2 主要操作流程

1. **选择级别和单元**：在主菜单选择要学习的级别和单元
2. **开始战斗**：点击"开始战斗"按钮进入游戏模式
3. **答题**：回答出现的英语题目
4. **击败怪兽**：通过答对题目减少怪兽生命值
5. **获得奖励**：通关后获得能量和星星奖励
6. **解锁新怪兽**：根据表现解锁新的怪兽
7. **口语练习**：进入口语模式练习发音
8. **查看错题本**：查看和复习答错的题目
9. **完成每日任务**：完成每日任务获得额外奖励

## 8. 特色功能

### 8.1 游戏化学习
- 奥特曼主题，吸引儿童兴趣
- 怪兽战斗系统，增加学习趣味性
- 积分和升级系统，提供学习动力
- 成就系统，鼓励持续学习

### 8.2 多维度学习
- 词汇学习：单词和句子
- 听力练习：语音合成
- 口语练习：语音识别
- 情景对话：真实场景对话练习

### 8.3 个性化学习
- 错题本：针对性复习
- 薄弱点专项练习
- 学习统计：跟踪学习进度
- 每日任务：保持学习习惯

### 8.4 技术亮点
- 响应式设计：适配不同设备
- 语音技术：Web Speech API应用
- 动画效果：流畅的游戏体验
- 数据管理：本地存储和导入导出

## 9. 未来优化方向

1. **多语言支持**：增加更多语言版本
2. **在线同步**：云存储游戏进度
3. **多人对战**：增加 multiplayer 模式
4. **更多教材**：支持更多英语教材
5. **AI助手**：智能学习建议
6. **家长监控**：学习数据报告
7. **游戏扩展**：更多游戏模式和怪兽
8. **性能优化**：减少资源占用，提高加载速度

## 10. 总结

**赛罗奥特曼英语大作战**是一个创新的英语学习游戏，通过游戏化的方式激发儿童学习兴趣，提高学习效果。项目采用纯前端技术实现，无需后端支持，便于部署和使用。

游戏融合了多种学习模式和游戏元素，包括单词学习、口语练习、怪兽养成、成就系统等，为儿童提供了一个全面而有趣的英语学习环境。

通过不断优化和扩展，该项目有潜力成为儿童英语学习的重要工具，帮助更多孩子在轻松愉快的氛围中学习英语。