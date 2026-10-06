# 高中化学 · 教学工具索引

本仓库是 [xmmmymm](https://github.com/xmmmymm) 名下各教学项目的**导航索引**，本身不含代码。
所有项目保持独立仓库、独立发布，按「知识点」而非「技术栈」划分，便于单点取用与课堂分发。

> 收录规则：一个项目 = 一个独立仓库 = 一项独立可用的教学工具。相似项目不合并，改为在此处互相索引。

---

## 一、交互式可视化（3D / 粒子模拟，浏览器直接打开）

面向课堂投屏与学生自学。**双击 `index.html` 即可运行，无需安装、无需联网**，
Three.js r128 已随仓库内置；也可通过下方在线链接直接访问。

| 项目 | 知识点 | 技术形态 | 在线 |
|---|---|---|---|
| [electrolyte-ionization](https://github.com/xmmmymm/electrolyte-ionization) | 电解质的电离<br>必修一 §2 | Three.js 3D 微观动画 + 2D 宏观电路 | [在线](https://xmmmymm.github.io/electrolyte-ionization/) |
| [IonViz-Simulation](https://github.com/xmmmymm/IonViz-Simulation) | 弱电解质电离平衡<br>电离度 α / Ka / pH | Canvas 2D 粒子级实时模拟 | [在线](https://xmmmymm.github.io/IonViz-Simulation/) |
| [atom-structure-3d](https://github.com/xmmmymm/atom-structure-3d) | 原子结构与核外电子排布<br>五种原子模型演变 | Three.js 3D + Canvas 2D | [在线](https://xmmmymm.github.io/atom-structure-3d/) |
| [colloid-chemistry-3d](https://github.com/xmmmymm/colloid-chemistry-3d) | 胶体的本质认识<br>丁达尔 / 聚沉 / 电泳 / 渗析 | Three.js 3D 微观仿真（6 个主题页） | [在线](https://xmmmymm.github.io/colloid-chemistry-3d/) |
| [molar-volume-3d](https://github.com/xmmmymm/molar-volume-3d) | 气体摩尔体积<br>PV=nRT 与 Vm | Three.js 3D（7 个预设实验） | [在线](https://xmmmymm.github.io/molar-volume-3d/) |
| [chem-reaction-3d](https://github.com/xmmmymm/chem-reaction-3d) | 化学反应微观机理<br>**289 个方程式 / 5 册** | Three.js 断键成键动画 + KaTeX | [在线](https://xmmmymm.github.io/chem-reaction-3d/) |

**「电解质电离」两个项目如何配合使用**

二者知识点互补，不重复，建议对照讲授：

- [electrolyte-ionization](https://github.com/xmmmymm/electrolyte-ionization) 解决**「强电解质为什么在固态有离子却不导电、溶解或熔融后才导电」**
  —— 含蔗糖不电离对照、NaCl 801 ℃ 熔融、晶格内部结构、水分子极性取向；
- [IonViz-Simulation](https://github.com/xmmmymm/IonViz-Simulation) 解决**「弱电解质电离平衡是动态的，以及浓度/温度如何影响电离度」**
  —— 含正逆反应速率双柱、温度联动 Ka、浓度联动 α、HCl 与 CH₃COOH 并排对比、氨水弱碱。

## 二、组卷与出题工具

面向教师日常备课出题。**均为本地离线工具**，数据存在本地，不联网。

| 项目 | 用途 | 形态 |
|---|---|---|
| [chemistry-equation-printer](https://github.com/xmmmymm/chemistry-equation-printer) | 化学方程式题库组卷打印：392 条人教版方程式、5 种题型、题目卷+答案卷 PDF 导出 | Electron 桌面应用（Windows 安装包 / 免安装版） |
| [xkw-toolkit](https://github.com/xmmmymm/xkw-toolkit) | 学科网（zxxk.com）教师工作流自动化：检索、批量加购、抽题攒库、组卷方案、导出 Word、去水印 | Python + CDP 附加已登录 Chrome（网校通会员适用） |

**出题链路可串成一条线**

```
xkw-toolkit 线A 检索加购   ──┐
                             ├──→  组卷  ──→  chemistry-equation-printer 排版打印
xkw-toolkit 线B 抽题攒库   ──┘
```

两者的方程式题库均为独立维护：xkw-toolkit 走**站内抓取**（实时、依赖平台），
chemistry-equation-printer 用**内置教材题库**（392 条、可离线、已机器校验配平与守恒）。

## 三、其他

| 项目 | 用途 | 形态 |
|---|---|---|
| [proportional-bar-generator](https://github.com/xmmmymm/proportional-bar-generator) | 比例条生成器：生成无缝矢量横向比例条，导出 SVG/PNG/JPG/BMP/TIFF/PDF，用于学术绘图与设计 | Vite + React + Electron（与化学教学无关） |

---

## 统一技术约定

这批项目由同一套约定贯穿，新增项目请遵循：

1. **完全离线**：页面不请求任何外部资源，所有第三方库（Three.js r128、KaTeX、Tailwind）随仓库内置。
   删除 `vendor/` 后页面仍可打开并给出降级提示，不静默白屏。
2. **构建方式**：
   - 纯前端教学页 → **零构建**，传统 `<script>` 标签（非 ES Module），保证 `file://` 协议下双击可用；
   - 桌面工具 → Node.js ≥ 18 + Electron，运行期离线，仅构建/打包阶段需网络。
3. **第三方库版本**：Three.js 统一锁定 **r128**（最后一个提供 UMD 版的版本），保证 `<script>` 方式可用。
4. **许可**：一律 MIT。
5. **在线演示**：通过 GitHub Pages 发布，README 顶部给出在线链接。

## 仓库一览

| 仓库 | 语言 | 提交 | 许可 | 分支 | Pages |
|---|---|---:|---|---|:--:|
| electrolyte-ionization | JavaScript | 2 | MIT | main | ✅ |
| IonViz-Simulation | TypeScript | 11 | MIT | main | ✅ |
| atom-structure-3d | JavaScript | 8 | MIT | main | ✅ |
| colloid-chemistry-3d | JavaScript | 2 | MIT | main | ✅ |
| molar-volume-3d | JavaScript | 2 | MIT | main | ✅ |
| chem-reaction-3d | HTML | 6 | MIT | master | ✅ |
| chemistry-equation-printer | JavaScript | 5 | MIT | main | — |
| xkw-toolkit | JavaScript / Python | 1 | MIT（部分第三方另行授权） | main | — |
| proportional-bar-generator | TypeScript | 3 | — | main | — |

<sub>数据截至 2026-10-06，由 `gh` CLI 实测采集。</sub>
