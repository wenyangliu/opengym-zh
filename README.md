# openGym 中文动作库

健身动作数据库，**5632 个动作**，字段名英文、内容全中文。供 AI 大模型 / 应用直接读取。

数据取自 [openGym](https://github.com/DuarteSantos8/openGym) 的 `catalogue/exercises`，翻译为中文后重新整理。

## 文件结构

| 文件 | 大小 | 说明 |
|:---|---:|:---|
| `exercises.json` | 1.3 MB | 全部 5632 条 |
| `parts/part_*.json` | 15–363 KB | 按身体部位拆分（11 个） |
| `chunks/chunk_01..29.json` | 约 44 KB | 每 200 条一块，**推荐 AI 读取用** |

## 数据格式

```json
{
  "id": "0025",
  "name": "杠铃卧推",
  "bodyPart": "胸部",
  "equipment": "杠铃",
  "target": "胸大肌",
  "category": "力量",
  "description": "经典的平卧推。把杠铃放到胸前，然后向上推，锻炼胸部、肩膀和三头肌。"
}
```

七个字段：`id` / `name` / `bodyPart` / `equipment` / `target` / `category` / `description`。

## 字段取值（全部中文，可直接枚举）

**bodyPart**：胸部 / 背部 / 大腿 / 腰部 / 肩部 / 上臂 / 前臂 / 小腿 / 颈部 / 全身 / 有氧

**category**：力量 / 自重训练 / 拉伸 / 灵活性 / 增强式训练 / 等长训练 / 有氧 / 瑜伽 / 奥林匹克举重 / 普拉提 / 康复 / 格斗

**equipment**：自重 / 哑铃 / 杠铃 / 绳索/龙门架 / 壶铃 / 弹力带 / 阻力带 / 史密斯机 / 杠杆式器械 / 瑞士球 / 药球 / 沙袋 / 悬吊训练带 / 泡沫轴 / 按摩球 / 负重 等 34 种

**target**：腹肌 / 胸大肌 / 背阔肌 / 股四头肌 / 腘绳肌 / 臀肌 / 三角肌 / 肱二头肌 / 肱三头肌 / 小腿肌 / 斜方肌 / 上背 / 前臂 / 内收肌 / 外展肌 / 前锯肌 / 肩胛提肌 / 脊柱 / 心血管系统

## 怎么给 AI 用

1.3 MB 对多数模型的上下文仍偏大，按需取用：

- **只想知道有哪些动作** → 读 `chunks/` 里的一块（44 KB，约 1.5 万 token）
- **要某个部位的全部动作** → `parts/part_chest.json`（111 KB）
- **要全量做检索/建索引** → `exercises.json`，或循环拉取 29 个 chunk

`chunks/` 按 `id` 顺序切分，每块 200 条，是最适合单次读取的粒度。

## 数据来源与许可

- 原始数据：[openGym](https://github.com/DuarteSantos8/openGym)，AGPL-3.0
- 部分文字源自 ExerciseDB（MIT）
- 中文翻译为本仓库生成

沿用 openGym 的 AGPL-3.0 许可。动作配图与动画（`media/`）版权归 Gym visual，不在本仓库范围内。
