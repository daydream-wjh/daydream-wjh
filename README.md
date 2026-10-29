<div align="center">

# 王嘉豪 · daydream-wjh

**把繁琐的重复操作，做成点一下就能用的工具**

南昌大学 · 深度学习 / 强化学习 · Java 后端

<img src="https://komarev.com/ghpvc/?username=daydream-wjh&label=VISITORS&color=2459d3&style=flat-square" alt="visitors">

</div>

---

## ⭐ 三个最值得先看的仓库

### 1. [配电网告警快速查询](https://github.com/daydream-wjh/distribution-alarm-query) · 单文件网页工具

<img src="https://raw.githubusercontent.com/daydream-wjh/distribution-alarm-query/main/docs/preview.png" width="760" alt="配电网告警快速查询界面">

调度员查一条线路的接地告警，原本要在主站系统里依次选数据库、设时间、配条件，步骤多、告警杂。
这个工具把它压成 **选时间 → 选表 → 点查询** 三步。

- **一个 `index.html` 就是全部**：无构建、无 npm、无后端，拷过去双击就能用
- 支持 5 张告警表、动态筛选条件、Excel/CSV 导出、全量分批导出（可取消）
- 最实用的是「导入响应」：把已经拿到的响应文本粘进去离线解析，不用反复打接口
- 接口返回形态在不同版本主站上不统一，做了 `XML → JSON → 分隔符文本` 多层解析兜底

> 适合：做电力/工控类内部工具，或者想看看「单文件交付」能做成什么样的人。

---

### 2. [dsh-opencode-go-usage](https://github.com/daydream-wjh/dsh-opencode-go-usage) · DeepSeek Harness 插件

<img src="https://raw.githubusercontent.com/daydream-wjh/dsh-opencode-go-usage/main/docs/preview.png" width="760" alt="OpenCode Go 限额读数">

在 DSH 输入框上方常驻一行额度读数：滚动 / 本周 / 本月三条窗口用了多少、最近一次重置还剩多久。

- 不用另开标签页、也不用等请求失败才发现额度用完了
- 主进程与渲染进程分离，60s 轮询 + 20s 缓存 + 并发合并，读失败不污染缓存
- 带 12 个用例的测试，CI 在 Node 22/24 上跑

> 适合：在写 DSH 插件、想参考一个完整插件（路由 + 客户端 + 测试 + CI）的人。

---

### 3. [mnist-realtime-recognition](https://github.com/daydream-wjh/mnist-realtime-recognition) · 手写数字实时识别

<img src="https://raw.githubusercontent.com/daydream-wjh/mnist-realtime-recognition/master/data/show.png" width="620" alt="实时手写数字识别">

浏览器画板上写一个数字，后端 ResNet18 立刻返回预测与置信度。经典的入门题，但把**从训练到部署的整条链路**都打通了。

- ResNet18 改单通道输入 + 7 段全连接头，训练脚本与推理服务都在仓库里
- 预处理链路（白底合成 → 灰度 → 反色 → Resize → Normalize）与训练严格对齐
- 无 GPU 自动降级到 CPU，装完依赖就能跑

> 适合：想要一个「能跑起来的 CV demo」当模板的人。

---

## 🀄 深度项目：麻将 AI

从规则引擎一路做到强化学习，同一套规则内核演进了四代 —— 也是我写得最久、最硬的一块。

| 阶段 | 做法 |
| --- | --- |
| ① 规则引擎 | 向听数 + 组合搜索树 + 宝牌番型计算，纯搜索不用模型 |
| ② 全信息引擎 | 加上对手剩余牌概率表，从「只看自己的牌」变成「能算别人手里还有什么」 |
| ③ 深度模型 | 用生产对局切高手动作做样本，Suphx 四通道牌面特征 + ResNet 预测弃胡 / 出牌 / 局面分数 |
| ④ 强化学习 | gymnasium 环境 + Suphx 特征 + PPO 自我对弈，策略网络用自定义 ResNet |

公开的两个仓库：

- **[mahjong-rl-trainer](https://github.com/daydream-wjh/mahjong-rl-trainer)** —— RL 主体：PPO2 + 自定义 ResNet 策略、Suphx 式特征提取、gym 环境封装
- **[sichuan-mahjong-rl](https://github.com/daydream-wjh/sichuan-mahjong-rl)** —— 四川麻将分支：定缺、换三张、27 张牌无吃

> 适合：对棋牌 AI、Suphx 特征编码、PPO 在非完全信息博弈上的应用感兴趣的人。

---

## 📦 全部仓库

### 👁️ 计算机视觉 / 深度学习

| 仓库 | 一句话 |
| --- | --- |
| [mnist-realtime-recognition](https://github.com/daydream-wjh/mnist-realtime-recognition) | 画板手写 → ResNet18 分类，Flask 一键跑起来 |
| [dlib-face-expression](https://github.com/daydream-wjh/dlib-face-expression) | 不训练网络，用 Dlib 68 点几何比例喂 KNN 做实时表情识别（2019 小组项目，已获软著）|
| [dlib-face-expression-v2](https://github.com/daydream-wjh/dlib-face-expression-v2) | 同上 2.0：几何特征做成 xlsx 数据集，横向对比四个分类器 + PSO 搜 SVM 超参 |
| [cgan-mnist](https://github.com/daydream-wjh/cgan-mnist) | 条件 GAN 生成 MNIST 手写数字，带逐轮生成样例与 Gradio 采样界面 |
| [brain-hemorrhage-edema-competition](https://github.com/daydream-wjh/brain-hemorrhage-edema-competition) | 脑出血 / 水肿影像数据竞赛：四张数据表的逐字段说明与探索性分析 |

### ⚡ 电力业务工具

| 仓库 | 一句话 |
| --- | --- |
| [distribution-alarm-query](https://github.com/daydream-wjh/distribution-alarm-query) | 配电网告警快速查询：单文件网页，多表筛选 + Excel 导出 + 响应离线解析 |

### 🧩 DeepSeek Harness 插件

| 仓库 | 一句话 |
| --- | --- |
| [dsh-opencode-go-usage](https://github.com/daydream-wjh/dsh-opencode-go-usage) | 输入框上方常驻 OpenCode Go 套餐限额读数 |
| [dsh-html-annotate](https://github.com/daydream-wjh/dsh-html-annotate) | 右侧栏 HTML 批注预览（fork）：框选后可拖动、八向缩放、方向键微调、Delete 删除 |

### ☕ Java 后端

| 仓库 | 一句话 |
| --- | --- |
| [shortlink](https://github.com/daydream-wjh/shortlink) | Java 17 + Spring Boot 3 多模块短链服务：网关 / 管理 / 跳转 / 聚合 + Vue3 控制台 |
| [xuecheng-plus](https://github.com/daydream-wjh/xuecheng-plus) | 在线教育微服务群：内容、媒资、搜索、认证、网关，配置托管 Nacos |
| [tlias-smart-learning](https://github.com/daydream-wjh/tlias-smart-learning) | Tlias 智能学习辅助系统：部门/员工管理、JWT 登录、OSS 上传、事务与 AOP 示例 |

### 📚 Java 与算法练习

| 仓库 | 一句话 |
| --- | --- |
| [leetcode](https://github.com/daydream-wjh/leetcode) | 202 道力扣题解，按 13 个主题索引，可直接当索引查 |
| [java](https://github.com/daydream-wjh/java) | Java 基础学习代码（集合、IO、多线程、网络编程、学生管理系统）|
| [puzzle-game](https://github.com/daydream-wjh/puzzle-game) | Swing 滑块拼图：3/4/5 三档难度、计时、最佳纪录、撤销、鼠标操作，界面全自绘 |
| [jedis](https://github.com/daydream-wjh/jedis) | 最小 Jedis 入门 demo |

---

## 🤝 支持

如果这里的某个仓库帮你省了点时间、或者给过你思路，**点个 ⭐ Star** 是最直接的支持 ——
也让我知道接下来该把精力放在哪个项目上。

有问题、建议、或者想让我补充某方面的文档，开个 issue 就行，我都会看。

<sub>所有仓库的 README 都是照着代码实际内容写的，包括已知问题与踩过的坑，不会只写漂亮话。</sub>
