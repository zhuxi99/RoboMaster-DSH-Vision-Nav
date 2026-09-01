# RoboMaster-DSH-Fire 战队专享 AI 研发套件（视觉组 & 导航组指南）

> **项目开源地址**：[https://github.com/zhuxi99/Robomaster-DSH-Fire](https://github.com/zhuxi99/Robomaster-DSH-Fire)  
> **战队专享打包下载**：[百度网盘下载链接](https://pan.baidu.com/s/1KiMcEniXDyrCK3-jsLx78g?pwd=4ivr) （提取码：`4ivr`）

---

## 🎯 为什么视觉组 & 导航组需要 DSH Desktop？

在 RoboMaster 算法与工程开发中，视觉组（传统视觉/深度学习装甲板检测、PnP 测距、能量机关预测、相机标定）与导航组（ROS/ROS2 导航栈、SLAM 建图、雷达与里程计融合、Fast-LIO、行为树规划）常常面临复杂的调试与代码协同痛点。

**Robomaster-DSH-Fire** 结合 DeepSeek Harness 桌面端，为战队打造了专属 AI 智能体研发环境：
1. **算法与工程级辅助**：内置 26 项工程与视觉专属 Skills（如 `rm-opencv-coach`、`senior-computer-vision`、`opencv-trackbar-tune`、`diagnosing-bugs` 等），支持从装甲板四点拟合、Trackbar 实时调参到 ROS 节点架构设计的全流程指导。
2. **长效记忆与知识图谱**：内置 `graph-memory` 与 `dsh-robomaster-core`，每次调试的坑点、踩雷记录和关键参数会自动沉淀为图谱记忆，跨会话、跨任务不丢失。
3. **开箱即用无缝分发**：集成了完整的前后端运行时与 Node/C++ 依赖，无需队员在本地重新配置复杂的原生编译环境。

---

## 📦 极速下载与解压说明

1. 打开百度网盘链接下载打包文件：  
   👉 **下载链接**：[https://pan.baidu.com/s/1KiMcEniXDyrCK3-jsLx78g?pwd=4ivr](https://pan.baidu.com/s/1KiMcEniXDyrCK3-jsLx78g?pwd=4ivr) （提取码：`4ivr`）

2. **重要：更改文件后缀名**  
   从百度网盘下载下来的文件是txt格式，是因为这个利用了些许漏洞，可以加速网盘下载，不用充会员了就，**请手动将文件后缀名修改为 `.tar`**（例如重命名为 `dsh-release.tar`）。

3. **解压文件**：
   ```bash
   # 新建解压目录并解压
   mkdir -p ~/dsh-release && tar -xf dsh-release.tar -C ~/dsh-release
   cd ~/dsh-release

   # 解压内部环境包
   tar -xf deepseek-harness-desktop-team-dist.tar
   ```

---

## 🚀 一键部署与运行步骤

### 1. 运行一键安装脚本
在解压后的目录中执行：
```bash
bash install.sh
```
*脚本会自动将桌面端环境部署至 `~/deepseek-harness-desktop`，并将战队专属插件、Agent 预设和 26 项 Skills 导入至本地系统。*

### 2. 配置个人 API 密钥（API Key）
为保障各队员的个人账户与额度安全，分发包内对 API 密钥进行了脱敏。请使用文本编辑器打开凭证文件：
```bash
nano ~/.dsh/.credentials.yaml
# 或使用 VS Code 打开 ~/.dsh/.credentials.yaml
```
根据自己常用的模型服务商，将对应的 `sk-your-key-here` 替换为你的真实 API Key（例如 DeepSeek、Grok 或其他中转平台的 Key）并保存。

### 3. 启动桌面端
配置完成后，在终端直接运行：
```bash
dsh-desktop
```
或执行：
```bash
~/deepseek-harness-desktop/start.sh
```

---

## 💡 视觉组 & 导航组常用能力与场景

- **装甲板识别与调参（视觉组）**：
  直接呼叫 `rm-opencv-coach` 或 `opencv-trackbar-tune` 技能，AI 可辅助编写滑动条调试 HSV 阈值、二值化、轮廓筛选与多边形拟合逻辑。
- **PnP 与坐标变换分析（视觉组）**：
  针对相机内参标定、外参转换、旋转矩阵与四元数转换提供数学公式与 OpenCV/Eigen 实现。
- **ROS/ROS2 节点与导航栈调试（导航组）**：
  协助分析 Costmap 配置、Navigation2 行为树（BehaviorTree）、TF 坐标系树异常及雷达点云滤波。
- **项目提示词更新说明**：
  战队定制提示词（Prompt Presets）后续会通过群内发布 JSON 文件的方式持续迭代，导入即可同步最新战队规则与比赛规范，无需重新打包。

---

> 遇到问题可联系视觉/导航组负责人，或在项目仓库 [Robomaster-DSH-Fire](https://github.com/zhuxi99/Robomaster-DSH-Fire) 提交 Issue。
