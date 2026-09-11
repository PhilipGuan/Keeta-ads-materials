# Keeta Advertising BD One-Pager — 国家复刻指南

> 基于 UAE 版（Keeta_Advertising_OnePager_UAE）确立的范式，供 KWT / QAT / BAH 等其他国家创编时使用。
> 模板源文件：`keeta-ads/src/one_pager_uae_template.html`（所有国家版本的唯一修改源头）。

---

## 一、这套 One-Pager 是什么

单页 A4（210×296mm）BD 销售物料，HTML + 双语 PDF（EN / AR 各一份）三件套：

- **HTML**：交互版，右上角 EN/عربية 一键切换，含可点击的 CTA 按钮（跳转该国商家登录页）和按钮呼吸动效。
- **PDF ×2**：由 HTML 分别以英文、阿语态导出，静态、无动效，打印和发商家用。

页面结构（从上到下）：品牌页头（含 4 个 KPI 卡）→ 三大价值点 → 广告版位（2 图 + 3 要点）→ 费用/回报双卡 → 异议应对 ×3 → CTA 深色横条 → 免责脚注。

---

## 二、已确立的标准（复刻时直接沿用，不要改）

### 1. 国家与命名体系

| 项目 | 标准 |
|---|---|
| 国家分组 | KSA 单独成版（Traffic Boost 话术）；UAE/KWT/QAT/BAH 统一用 **Advertising** 话术 |
| 文件命名 | `Keeta_Advertising_OnePager_{国家}.html` / `_EN.pdf` / `_AR.pdf`（如 `_KWT`） |
| 货币配置 | UAE: AED，KWT: KWD，QAT: QAR，BAH: BHD（存于模板 `CONFIG.currency`，当前文案无金额，仅备用） |
| 登录链接 | `https://merchant.mykeeta.com/pc/login?region={代码}`，由 `CONFIG.region` 驱动 |
| 图片命名 | `{country}_{slot}.png`，全小写英文，EN/AR 共用同一张图（无需分语言出图） |

**region 代码实测结论**：`AE`→阿联酋登录页 ✅、`KW`→科威特 ✅、`SA`→沙特 ✅；`QA`、`BH` 目前返回空白页（商家门户未上线），**QAT/BAH 版上线前需业务确认门户已就绪**。

### 2. 设计规范（Design Tokens）

| 用途 | 色值 |
|---|---|
| Keeta 黄（页头、按钮） | `#FFD100` |
| 深色墨（文字、深色块） | `#17181C` |
| 品牌绿（Return 卡片头、标题高亮） | `#00A870` |
| 标题高亮底纹（EN/AR 统一） | `rgba(0,168,112,.65)`（65% 透明度荧光笔效果） |
| ROI 横幅浅绿底纹 | `#EAF7F1` |
| 辅助灰 | `#5B6067` |

其他视觉规范：阿语整体 RTL（作用于 `.page` 的 `dir` 属性，**不要**设在 `<html>` 上）；拉丁文指标（4x+ 等）在 RTL 语境中必须包 `<span dir="ltr">` 隔离，否则 "4x+" 会显示成 "+4x"；阿语字体族用 Geeza Pro 优先。

### 3. 文案基线（九项已定稿修改）

1. 副标题："Advertising boosts your restaurants to better positions on Keeta — in the store list, homepage icons and search."
2. ROI 指标统一 "**4x+**"（不是 2–4x）
3. KPI："You set the **cost cap** / you control the budget"（无具体金额，最低预算 SAR 350 类字样已删）
4. "**Premium** placements, all day"
5. "jumps to **premium** positions"
6. CTA 文案："Questions? Contact your Keeta BD — we're more than happy to help!"（礼貌专业版）
7. 已删除 "than mature platforms" 横向对比（其他国家的 Early-mover 卖点保留，但不做平台间比较）
8. WHERE 黑底黄字徽章已删除（与标题重复）
9. CTA 按钮 "Activate Advertising" 可点击，带 2.4s 呼吸脉冲动效（hover 放大+光晕；`prefers-reduced-motion` 自动关闭；导出 PDF 时临时禁用动效保证静态完整）

### 4. 阿语本地化规则

**术语表**（广告专业术语保留英文，其余本地化）：

| 英文 | 阿语 | 备注 |
|---|---|---|
| Advertising | الإعلانات | 非人复数，作主语时动词用阴性单数（ترتقي / تثبّت / وتصل） |
| Activate | فعِّل | 命令式，与 CTA 按钮统一 |
| Keeta Partner | شريك كيتا | 正偏组合，被属格词在前 |
| CTA 按钮 | فعِّل الإعلانات | |
| ROAS / CPC / ROI / Automatic bidding / T+1 / Keeta / BD | 保留英文 | 按此前约定 |

页面中**不应残留任何英文说明性词汇**（已逐一清理，复刻时注意新国家名也要给阿语写法）。

---

## 三、创编一个新国家，需要你提供什么

以 KWT 为例（QAT/BAH 同理）：

1. **两张版位配图**（放入对应 output 文件夹）：
   - `{country}_placement_list.png` — 店铺列表排名靠前 + "AD" 标记的示意截图
   - `{country}_placement_search.png` — 搜索与首页版位的示意截图
   - 建议竖向比例、分辨率 ≥300px 宽；无图时可沿用 UAE 示意图并保留 "illustrative" 免责说明
2. **确认 region 代码可用**：我会先用浏览器实测 `region=KW` 等能否打开该国登录页（QA/BH 目前不行，需等门户上线）
3. **国家名双语文案**：阿语国名（الكويت / قطر / البحرين），用于顶栏 `brand_name`；英文我方补齐
4. **业务口径确认**（如有变化）：ROI 参考区间 4x+ 是否适用该国、有无国家专属政策（如新店扶持周期、Voucher 计划）

不需要你提供：货币（已定）、设计/排版（沿用）、阿语翻译（我方出稿并做语法校对，你审核即可）。

---

## 四、我的标准工作流（每个国家约 6 步）

1. **复制模板**：以 `one_pager_uae_template.html` 为源，改 3 个 `CONFIG` 值（country / currency / region）+ 顶栏国名（EN/AR）+ CTA 链接 region 参数
2. **文案微调**：仅当有国家专属口径时调整；否则逐字沿用 UAE 基线（含阿语术语表）
3. **嵌图**：`{{IMG:placement_list}}` / `{{IMG:placement_search}}` 占位符替换为该国 PNG（白底合成 base64 嵌入，避免外链）
4. **渲染验证**：浏览器逐屏截图检查 EN/AR 两态——内容不溢出（自然高度 ≤1119px）、RTL 无反向字符、图片显示正常、CTA 链接指向正确
5. **导出 PDF**：794×1123 视口 → 隐藏语言按钮 + 禁用动效 + zoom=2 → 整页截图 → 组装单页 A4 PDF（EN、AR 各一份），校验尺寸 210×296mm
6. **交付清单**：每国 3 个文件（HTML + EN PDF + AR PDF），临时截图全部清理

---

## 五、当前进度与待办

| 国家 | One-Pager | Playbook | 待办 |
|---|---|---|---|
| KSA | ✅ 独立版（Traffic Boost 话术） | ✅ | — |
| UAE | ✅ 本指南的范式来源 | ✅（图片位仍是 UAE 示意图） | 等你上传 `uae_entry.png`、`uae_budget.png`、`uae_active.png`、`uae_app_dashboard.png` 后替换并重导 PDF |
| KWT | ⏳ 待启动 | ⏳ | 需要 KWT 两张版位图 |
| QAT | ⏳ 待启动 | ⏳ | region=QA 门户空白，需确认上线时间 |
| BAH | ⏳ 待启动 | ⏳ | region=BH 门户空白，需确认上线时间 |

**独立后续任务**（你提出、另行启动）：Vouchers / Free Trial Card 各国海报。

---

## 六、注意事项（踩过的坑）

- 固定高度页面内容溢出时元素会被静默压缩（如页头消失），必须用 `.page > * { flex-shrink: 0 }` 并迭代压内容至自然高度达标
- RTL 截图偏移：`dir` 必须加在 `.page` 上且 `html, body` 定宽 210mm
- 拉丁指标在 RTL 中必须 `dir="ltr"` 隔离；KPI 副标题选择器要用 `.kpi > span`，否则会误伤隔离标签
- PDF 导出前必须禁用 CTA 动效，否则可能截到变形帧
- 用户上传的 PNG 若含透明通道，合成时必须垫白底，防止 PDF 内出现黑底
