# TPIsoftware 簡報網頁設計系統

> 依照此文件提供簡報大綱，即可生成風格一致的說明網頁。
> 所有元件、色調、字型、動效已完整記錄。

---

## 目錄

1. [基礎設定](#1-基礎設定)
2. [色彩系統](#2-色彩系統)
3. [字型系統](#3-字型系統)
4. [Logo 使用](#4-logo-使用)
5. [頁面結構](#5-頁面結構)
6. [元件庫](#6-元件庫)
7. [版面配置](#7-版面配置)
8. [動效與互動](#8-動效與互動)
9. [中英切換功能](#9-中英切換功能)
10. [簡報大綱格式](#10-簡報大綱格式)
11. [完整 HTML 模板](#11-完整-html-模板)

---

## 1. 基礎設定

```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>【頁面標題】｜TPIsoftware</title>
    <!-- 必要字型 -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&family=Noto+Sans+TC:wght@300;400;500;700&display=swap" rel="stylesheet">
</head>
```

**字型優先順序：** `'Inter', 'Noto Sans TC', 'Microsoft JhengHei', sans-serif`
- Inter → 英文、數字（支援 300–900 weight）
- Noto Sans TC → 中文（支援 300–700 weight）

---

## 2. 色彩系統

貼入 `:root` 區塊，所有元件均使用這組變數：

```css
:root {
    /* ── 主色（紫） ── */
    --primary:          #5B21B6;   /* 深紫，用於背景、漸層起點 */
    --primary-light:    #7C3AED;   /* 主紫，最常用（按鈕、標籤、重點） */
    --primary-glow:     #8B5CF6;   /* 亮紫，hover 光暈 */
    --primary-pale:     #EDE9FE;   /* 淡紫背景（section-tag、highlight） */
    --primary-pale2:    #F5F3FF;   /* 更淡紫（question-box 背景） */

    /* ── 輔助色（藍） ── */
    --accent:           #0EA5E9;   /* 天藍，漸層終點、裝飾線 */
    --accent-dark:      #0284C7;   /* 深藍，info 相關 */

    /* ── 文字色 ── */
    --secondary:        #475569;
    --dark:             #0F172A;   /* 主文字，幾乎黑 */
    --text-secondary:   #475569;   /* 次要文字 */
    --text-muted:       #94A3B8;   /* 輔助文字 */

    /* ── 狀態色 ── */
    --success:          #059669;   /* 綠，card-success 頂邊 */
    --success-bg:       #ECFDF5;
    --success-border:   #A7F3D0;
    --warning:          #DC2626;   /* 紅，card-warning 頂邊 */
    --warning-bg:       #FEF2F2;
    --warning-border:   #FECACA;
    --info:             #0284C7;   /* 藍，card-info 頂邊 */
    --info-bg:          #F0F9FF;
    --info-border:      #BAE6FD;

    /* ── 背景 / 邊框 ── */
    --bg-base:          #FFFFFF;
    --bg-subtle:        #F8FAFC;   /* 淡灰背景（flow-diagram、timeline） */
    --bg-muted:         #F1F5F9;
    --border:           #E2E8F0;   /* 標準邊框 */
    --border-strong:    #CBD5E1;   /* 加重邊框 */
}
```

### 色彩使用原則

| 情境 | 色彩 |
|------|------|
| 主要互動（按鈕、標籤、圓點） | `--primary-light` #7C3AED |
| Hero 漸層標題 | `135deg, #3B0764 → #7C3AED → #0EA5E9` |
| Key Point 漸層背景 | `135deg, #5B21B6 → #4338CA` |
| CTA 深色背景 | `135deg, #3B0764 → #1E1B4B → #0C4A6E` |
| Footer 背景 | `#0F172A` |
| 正面/成功 | `--success` #059669 |
| 警示/對比 | `--warning` #DC2626 |
| 資訊/流程 | `--info` #0284C7 |

---

## 3. 字型系統

```css
/* 全域基礎 */
body {
    font-family: 'Inter', 'Noto Sans TC', 'Microsoft JhengHei', sans-serif;
    color: var(--dark);
    background: #FFFFFF;
    line-height: 1.6;
    -webkit-font-smoothing: antialiased;
}

/* Hero 主標題 */
.hero-title {
    font-size: 54px;        /* 手機: 34px */
    font-weight: 800;
    letter-spacing: -2px;
    line-height: 1.15;
    background: linear-gradient(135deg, #3B0764 0%, #7C3AED 45%, #0EA5E9 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
}

/* Section 標題 */
.section-title  { font-size: 23px; font-weight: 700; letter-spacing: -0.3px; }

/* 子標題 h3 */
h3              { font-size: 17px; font-weight: 700; letter-spacing: -0.2px; }

/* 小標題 h4 */
h4              { font-size: 15px; font-weight: 600; color: var(--text-secondary); }

/* 內文 */
body            { font-size: 15px; line-height: 1.6; }

/* 標籤 */
.section-tag    { font-size: 11px; font-weight: 700; letter-spacing: 1.2px; text-transform: uppercase; }

/* CTA 標題 */
.cta-title      { font-size: 38px; font-weight: 800; letter-spacing: -0.8px; }
```

---

## 4. Logo 使用

### 檔案位置
```
images/
  logo-zh.png   ← 中文版「昕力資訊」（預設顯示）
  logo-en.png   ← 英文版「TPI SOFTWARE」（切英文時顯示）
```

### Navbar Logo HTML
```html
<div class="logo-section">
    <img id="logo-zh" src="images/logo-zh.png" alt="昕力資訊" style="height:40px;">
    <img id="logo-en" src="images/logo-en.png" alt="TPIsoftware" style="height:40px; display:none;">
</div>
```

### Logo CSS
```css
.logo-section {
    display: flex;
    align-items: center;
    gap: 12px;
}
.logo-section img {
    height: 38px;
    max-width: 160px;
    object-fit: contain;
}
```

> **規則：** 語言切換時 JS 同步切換兩個 logo 的 `display`

---

## 5. 頁面結構

```
┌─────────────────────────────────────────┐
│  NAVBAR  (sticky, height: 68px)         │  ← logo + 語言切換 + CTA 按鈕
├─────────────────────────────────────────┤
│  HERO    (padding: 80px 40px 88px)      │  ← badge + 主標題 + 副標題 + trust badges
│  背景：白色格線紋理                       │
├─────────────────────────────────────────┤
│  CONTAINER (max-width: 1200px)          │
│  ┌─────────────────────────────────┐    │
│  │  SECTION 1  (白底圓角卡片)       │    │  ← tag + title + 內容
│  │  SECTION 2                      │    │
│  │  ...                            │    │
│  │  SECTION N                      │    │
│  └─────────────────────────────────┘    │
├─────────────────────────────────────────┤
│  CTA SECTION (深色漸層)                  │  ← eyebrow + title + desc + 2 buttons
├─────────────────────────────────────────┤
│  FOOTER (深色 #0F172A)                  │  ← 3欄 grid + copyright
└─────────────────────────────────────────┘
```

---

## 6. 元件庫

### 6.1 Navbar

```html
<header>
    <div class="logo-section">
        <img id="logo-zh" src="images/logo-zh.png" alt="昕力資訊" style="height:40px;">
        <img id="logo-en" src="images/logo-en.png" alt="TPIsoftware" style="height:40px; display:none;">
    </div>
    <nav class="header-nav">
        <button class="lang-toggle" onclick="toggleLang()" aria-label="Switch language">EN</button>
        <a href="聯絡連結" target="_blank" class="nav-cta">聯絡我們</a>
    </nav>
</header>
```

---

### 6.2 Hero Section

```html
<div class="hero">
    <div class="hero-inner">
        <!-- 頂部小標籤 badge -->
        <div class="hero-badge">
            <span class="hero-badge-dot"></span>
            【副標籤文字，例如：產品名稱 × 公司名稱】
        </div>

        <!-- 主標題（漸層色） -->
        <h1 class="hero-title">【主標題】</h1>

        <!-- 副標題（斜體灰色） -->
        <p class="hero-subtitle">【副標題，建議用英文 slogan】</p>

        <!-- 底部三個信任標籤 -->
        <div class="trust-badges">
            <span class="trust-badge">【標籤 1】</span>
            <span class="trust-badge">【標籤 2】</span>
            <span class="trust-badge">【標籤 3】</span>
        </div>
    </div>
</div>
```

---

### 6.3 Section 卡片

每一頁簡報對應一個 section：

```html
<div class="section">
    <!-- 標頭（必要） -->
    <div class="section-header">
        <span class="section-tag">【分類標籤，如：AI 趨勢】</span>
        <h2 class="section-title">【章節標題】</h2>
    </div>

    <!-- 以下為內容元件，依需求組合 -->

</div>
```

---

### 6.4 Question Box（情境問題框）

用於模擬客戶提問、引導情境：

```html
<div class="question-box">
    <div class="question-icon">💭</div>
    <div class="question-text">「【問題或情境描述】」</div>
</div>
```

---

### 6.5 Bullet List（項目清單）

```html
<ul class="bullet-list">
    <li>【項目一】</li>
    <li>【項目二】</li>
    <li>【項目三】</li>
</ul>
```

> 每個 `li` 前自動加紫色圓點，無需手動加符號

---

### 6.6 Numbered Steps（數字步驟清單）

```html
<ol class="numbered-steps">
    <li>【步驟一說明】</li>
    <li>【步驟二說明】</li>
    <li>【步驟三說明】</li>
</ol>
```

> 自動產生紫色圓形數字

---

### 6.7 Key Point（重點強調框）

深紫漸層背景，白色文字，用於頁面結語或最重要觀點：

```html
<div class="key-point">
    【最重要的一句話結論】
</div>
```

---

### 6.8 Cards（資訊卡片）

四種語意色系，頂端有 3px 色條：

```html
<!-- 中性強調（紫色） -->
<div class="card card-emphasis">
    <div class="card-title">【標題】</div>
    <p>【內容】</p>
</div>

<!-- 正面/成功（綠色） -->
<div class="card card-success">
    <div class="card-title">【標題】</div>
    <p>【內容】</p>
</div>

<!-- 警示/對比（紅色） -->
<div class="card card-warning">
    <div class="card-title">【標題】</div>
    <p>【內容】</p>
</div>

<!-- 資訊/流程（藍色） -->
<div class="card card-info">
    <div class="card-title">【標題】</div>
    <p>【內容】</p>
</div>
```

---

### 6.9 Flow Diagram（流程圖）

橫向流程，box 之間用箭頭連接：

```html
<div class="flow-diagram">
    <div class="flow-box">【步驟一】</div>
    <div class="flow-arrow">→</div>
    <div class="flow-box">【步驟二】</div>
    <div class="flow-arrow">→</div>
    <!-- 最後一個可設為深色強調 -->
    <div class="flow-box" style="background: var(--primary); color: white; border-color: var(--primary);">
        【最終狀態】<br><small>（說明）</small>
    </div>
</div>

<!-- 縱向流程（加 flex-direction: column） -->
<div class="flow-diagram" style="flex-direction: column; gap: 6px;">
    <div class="flow-box" style="width: 75%; max-width: 380px;">【頂層】</div>
    <div class="flow-arrow" style="transform: rotate(90deg); margin: 6px 0;">→</div>
    <div class="flow-box" style="width: 75%; max-width: 380px; background: var(--primary); color: white; border-color: var(--primary);">【中層（強調）】</div>
    <div class="flow-arrow" style="transform: rotate(90deg); margin: 6px 0;">→</div>
    <div class="flow-box" style="width: 75%; max-width: 380px;">【底層】</div>
</div>
```

---

### 6.10 Timeline（時間軸）

用於多階段流程說明：

```html
<div class="timeline">
    <div class="timeline-item">
        <h4>① 【第一階段名稱】</h4>
        <p>【詳細說明文字】</p>
    </div>
    <div class="timeline-item">
        <h4>② 【第二階段名稱】</h4>
        <p>【詳細說明文字】</p>
    </div>
    <div class="timeline-item">
        <h4>③ 【第三階段名稱】</h4>
        <p>【詳細說明文字】</p>
    </div>
</div>
```

> 每個 item 左側有紫色 3px 邊條

---

### 6.11 Table（比較表格）

深色表頭，隔行淡灰，hover 變淡紫：

```html
<table>
    <thead>
        <tr>
            <th>【欄位一】</th>
            <th>【欄位二】</th>
            <th>【欄位三】</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><strong>【項目名稱】</strong></td>
            <td>【值 A】</td>
            <td>【值 B】</td>
        </tr>
        <!-- 更多行 -->
    </tbody>
</table>
```

---

### 6.12 Highlight Text（行內強調）

```html
<span class="highlight-text">【強調詞彙】</span>
```

> 淡紫背景 + 深紫文字，用於 bullet list 中標記關鍵詞

---

### 6.13 Before / After 比較

```html
<div class="ba-wrapper">
    <div class="ba-col ba-before">
        <div class="ba-label">
            <span class="ba-icon">✕</span>
            導入前
        </div>
        <ul class="ba-list">
            <li>【缺點一】</li>
            <li>【缺點二】</li>
            <li>【缺點三】</li>
        </ul>
    </div>
    <div class="ba-divider">→</div>
    <div class="ba-col ba-after">
        <div class="ba-label">
            <span class="ba-icon">✓</span>
            導入後
        </div>
        <ul class="ba-list">
            <li>【優點一】</li>
            <li>【優點二】</li>
            <li>【優點三】</li>
        </ul>
    </div>
</div>
```

---

### 6.14 Stats Grid（統計數字格）

```html
<div class="stats-grid">
    <div class="stat-item">
        <div class="stat-number">【數字，如：83%】</div>
        <div class="stat-label">【說明文字】</div>
    </div>
    <!-- 重複 stat-item，最多 5 個 -->
</div>
```

> 每個 stat-item 頂部有紫→藍漸層色條

---

### 6.15 Brand Tag Marquee（品牌跑馬燈）

用於展示客戶/合作夥伴名稱：

```html
<div class="logo-marquee-section">
    <!-- 第一排：向左跑 -->
    <div class="logo-marquee-row row-1">
        <span class="brand-tag">品牌 A</span>
        <span class="brand-tag">品牌 B</span>
        <!-- ...重複一次以達到無縫效果 -->
    </div>
    <!-- 第二排：向右跑 -->
    <div class="logo-marquee-row row-2">
        <span class="brand-tag">品牌 C</span>
        <span class="brand-tag">品牌 D</span>
        <!-- ...重複一次 -->
    </div>
</div>
```

> **注意：** 每排的 brand-tag 需複製兩份（原始 + 一份副本）才能形成無縫動畫

---

### 6.16 Testimonial Grid（客戶見證卡片）

3欄 × 2列的客戶見證網格（左欄跨兩列）：

```html
<div class="tg-wrapper">
    <!-- 主卡（左欄，跨 2 列） -->
    <div class="tg-card tg-card-main">
        <div class="tg-brand">
            <img class="tg-logo-img" src="【logo URL】" alt="【品牌名】">
        </div>
        <div class="tg-quote">「【引言】」</div>
        <div class="tg-author-name">【姓名】</div>
        <div class="tg-author-role">【職稱】</div>
        <div class="tg-stat-num">【大數字，如：100%】</div>
        <div class="tg-stat-label">【數字說明】</div>
    </div>

    <!-- 子卡（右側，各佔 1 格） -->
    <div class="tg-card tg-card-sub">
        <div class="tg-brand"><img class="tg-logo-img" src="【logo】" alt="【品牌】"></div>
        <div>
            <div class="tg-stat-num-sub">【數字，如：10x】</div>
            <div class="tg-stat-label">【說明】</div>
        </div>
    </div>
    <!-- 再加 3–4 個 tg-card tg-card-sub -->
</div>
```

---

### 6.17 CTA Section

```html
<div class="cta-section">
    <div class="cta-inner">
        <p class="cta-eyebrow">【上方小標，如：準備好了嗎？】</p>
        <h2 class="cta-title">【主 CTA 標題<br>可換行】</h2>
        <p class="cta-desc">【說明文字<br>可換行】</p>
        <div class="cta-buttons">
            <a href="【連結】" target="_blank" class="btn-cta-primary">【主要按鈕】</a>
            <a href="【連結】" target="_blank" class="btn-cta-secondary">【次要按鈕】</a>
        </div>
    </div>
</div>
```

---

### 6.18 Footer

```html
<footer>
    <div class="footer-inner">
        <!-- 欄 1：品牌 -->
        <div>
            <div class="footer-brand-name">TPIsoftware</div>
            <p class="footer-tagline">Your AI Partner for Mission-Critical Success</p>
            <p class="footer-desc">【品牌描述】</p>
        </div>

        <!-- 欄 2：服務 -->
        <div>
            <p class="footer-col-title">服務項目</p>
            <div class="footer-links">
                <a href="【連結】" target="_blank" class="footer-link">【服務一】</a>
                <a href="【連結】" target="_blank" class="footer-link">【服務二】</a>
            </div>
        </div>

        <!-- 欄 3：聯絡 -->
        <div>
            <p class="footer-col-title">聯絡我們</p>
            <div class="footer-links">
                <a href="【連結】" target="_blank" class="footer-link">【連結一】</a>
                <a href="【連結】" target="_blank" class="footer-link">【連結二】</a>
            </div>
        </div>
    </div>
    <div class="footer-bottom">
        <p>© 2026 TPIsoftware 昕力資訊股份有限公司. All rights reserved.</p>
    </div>
</footer>
```

---

## 7. 版面配置

### 兩欄 Grid
```html
<div class="two-column">
    <div><!-- 左欄內容 --></div>
    <div><!-- 右欄內容 --></div>
</div>
```

### 三欄 Grid
```html
<div class="three-column">
    <div class="card card-info"><!-- 卡片一 --></div>
    <div class="card card-info"><!-- 卡片二 --></div>
    <div class="card card-info"><!-- 卡片三 --></div>
</div>
```

### 搭配原則
- `two-column` + `card-warning` / `card-success` → 對比比較（優缺點）
- `three-column` + `card-info` → 三個面向說明
- `two-column` 內放 `bullet-list` → 分兩欄條列

---

## 8. 動效與互動

| 元件 | 動效 |
|------|------|
| `.section:hover` | `box-shadow: 0 4px 24px rgba(91,33,182,0.06)` |
| `.card:hover` | `box-shadow: 0 4px 20px rgba(0,0,0,0.06)` |
| `.nav-cta:hover` | `translateY(-1px)` + 紫色陰影 |
| `.btn-cta-primary:hover` | `translateY(-2px)` + 深陰影 |
| `.brand-tag:hover` | 背景變淡紫、文字變主紫 |
| `.logo-marquee-row.row-1` | `marquee-left 38s linear infinite`（向左滾動） |
| `.logo-marquee-row.row-2` | `marquee-right 38s linear infinite`（向右滾動） |
| `table tr:hover td` | 背景變 `var(--primary-pale)` |
| `html` | `scroll-behavior: smooth` |

---

## 9. 中英切換功能

### 原理
1. Navbar 右上有 `<button class="lang-toggle" onclick="toggleLang()">EN</button>`
2. 點擊觸發 JS `toggleLang()` → 切換 `isEn` 布林值 → 呼叫 `applyLang(isEn)`
3. `applyLang()` 使用 `document.querySelector` 依序替換每個元素的 `textContent` / `innerHTML`
4. Logo 同步切換（`logo-zh` / `logo-en` 的 `display`）
5. 按鈕文字在 `EN` / `中文` 之間切換

### JS 結構
```javascript
(function () {
    var isEn = false;

    function applyLang(en) {
        // Logo
        document.getElementById('logo-zh').style.display = en ? 'none' : '';
        document.getElementById('logo-en').style.display = en ? ''     : 'none';

        // Page title
        document.title = en ? '【英文標題】' : '【中文標題】';
        document.documentElement.lang = en ? 'en' : 'zh-TW';

        // 依序處理各區塊...
        // （詳見完整模板的 <script> 區塊）
    }

    window.toggleLang = function () {
        isEn = !isEn;
        applyLang(isEn);
        document.querySelector('.lang-toggle').textContent = isEn ? '中文' : 'EN';
    };
}());
```

### 新增翻譯的方法

在 `applyLang(en)` 函式內，找到對應的 section，加入：

```javascript
// 範例：替換某個 section 的 h3 標題
var mySection = secs[N]; // N = 第幾個 .section（從 0 開始）
mySection.querySelector('h3').textContent = en ? 'English Title' : '中文標題';

// 替換 bullet list
var bullets = en
    ? ['Point A', 'Point B', 'Point C']
    : ['要點一', '要點二', '要點三'];
mySection.querySelectorAll('.bullet-list li')
         .forEach(function(li, i) { li.textContent = bullets[i]; });
```

---

## 10. 簡報大綱格式

### 提供格式（給 AI 生成新頁面用）

```
# 簡報主題

## 基本資訊
- 標題（中）：【主標題】
- 標題（英）：【英文主標題】
- 副標題 Slogan（英）：【英文 slogan】
- 信任標籤：【標籤1】、【標籤2】、【標籤3】
- Hero Badge：【小標籤文字】
- 聯絡連結：https://...
- Logo：images/logo-zh.png / images/logo-en.png

## 章節一
- 分類標籤（中/英）：XX / XX
- 標題（中/英）：XX / XX
- 情境問題（中/英）：「XX」/ "XX"
- 重點清單（中/英）：
  - 點一（中）→ 點一（英）
  - 點二（中）→ 點二（英）
- 元件類型：bullet-list / flow-diagram / table / timeline / key-point
- Key Point（中/英）：XX / XX

## 章節二
...（同上格式）

## CTA 區塊
- Eyebrow（中/英）：XX / XX
- 標題（中/英）：XX / XX
- 說明（中/英）：XX / XX
- 主按鈕文字（中/英）：XX / XX 連結：https://...
- 次按鈕文字（中/英）：XX / XX 連結：https://...

## Footer
- 品牌描述（中/英）：XX / XX
- 服務欄標題（中/英）：XX / XX
- 服務清單（中/英）：XX/XX、XX/XX...
- 聯絡欄標題（中/英）：XX / XX
- 聯絡清單（中/英）：XX/XX、XX/XX...
```

---

## 11. 完整 HTML 模板

以下是可直接複製使用的最小可運作模板（2 個 section + CTA + Footer）：

```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>【頁面標題】｜TPIsoftware</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&family=Noto+Sans+TC:wght@300;400;500;700&display=swap" rel="stylesheet">
    <style>
        /* ─── 貼入完整 CSS（見上方色彩系統 + 字型系統 + 所有元件 CSS） ─── */
        /* 可直接從 chatgpt-enterprise-tech/index.html 的 <style> 區塊複製 */
    </style>
</head>
<body>

    <!-- ── Navbar ── -->
    <header>
        <div class="logo-section">
            <img id="logo-zh" src="images/logo-zh.png" alt="昕力資訊" style="height:40px;">
            <img id="logo-en" src="images/logo-en.png" alt="TPIsoftware" style="height:40px; display:none;">
        </div>
        <nav class="header-nav">
            <button class="lang-toggle" onclick="toggleLang()" aria-label="Switch language">EN</button>
            <a href="https://www.tpisoftware.com/contact" target="_blank" class="nav-cta">聯絡我們</a>
        </nav>
    </header>

    <!-- ── Hero ── -->
    <div class="hero">
        <div class="hero-inner">
            <div class="hero-badge">
                <span class="hero-badge-dot"></span>
                【Badge 文字】
            </div>
            <h1 class="hero-title">【主標題】</h1>
            <p class="hero-subtitle">【英文 Slogan】</p>
            <div class="trust-badges">
                <span class="trust-badge">【信任標籤一】</span>
                <span class="trust-badge">【信任標籤二】</span>
                <span class="trust-badge">【信任標籤三】</span>
            </div>
        </div>
    </div>

    <!-- ── 內容容器 ── -->
    <div class="container">

        <!-- 第 1 頁 -->
        <div class="section">
            <div class="section-header">
                <span class="section-tag">【分類】</span>
                <h2 class="section-title">【章節標題】</h2>
            </div>

            <div class="question-box">
                <div class="question-icon">💭</div>
                <div class="question-text">「【情境問題】」</div>
            </div>

            <ul class="bullet-list">
                <li>【要點一】</li>
                <li>【要點二】</li>
                <li>【要點三】</li>
            </ul>

            <div class="key-point">【結論一句話】</div>
        </div>

        <!-- 第 2 頁 -->
        <div class="section">
            <div class="section-header">
                <span class="section-tag">【分類】</span>
                <h2 class="section-title">【章節標題】</h2>
            </div>

            <h3>【子標題】</h3>

            <div class="two-column">
                <div class="card card-warning">
                    <div class="card-title">【對比項 A】</div>
                    <ul style="padding-left:20px; margin-top:10px;">
                        <li>【缺點一】</li>
                        <li>【缺點二】</li>
                    </ul>
                </div>
                <div class="card card-success">
                    <div class="card-title">【對比項 B】</div>
                    <ul style="padding-left:20px; margin-top:10px;">
                        <li>【優點一】</li>
                        <li>【優點二】</li>
                    </ul>
                </div>
            </div>
        </div>

    </div><!-- /.container -->

    <!-- ── CTA ── -->
    <div class="cta-section">
        <div class="cta-inner">
            <p class="cta-eyebrow">【Eyebrow】</p>
            <h2 class="cta-title">【CTA 主標題】</h2>
            <p class="cta-desc">【CTA 說明】</p>
            <div class="cta-buttons">
                <a href="https://www.tpisoftware.com/contact" target="_blank" class="btn-cta-primary">聯絡我們</a>
                <a href="https://www.tpisoftware.com" target="_blank" class="btn-cta-secondary">了解更多</a>
            </div>
        </div>
    </div>

    <!-- ── Footer ── -->
    <footer>
        <div class="footer-inner">
            <div>
                <div class="footer-brand-name">TPIsoftware</div>
                <p class="footer-tagline">Your AI Partner for Mission-Critical Success</p>
                <p class="footer-desc">【品牌描述】</p>
            </div>
            <div>
                <p class="footer-col-title">服務項目</p>
                <div class="footer-links">
                    <a href="https://www.tpisoftware.com" target="_blank" class="footer-link">【服務一】</a>
                    <a href="https://www.tpisoftware.com" target="_blank" class="footer-link">【服務二】</a>
                </div>
            </div>
            <div>
                <p class="footer-col-title">聯絡我們</p>
                <div class="footer-links">
                    <a href="https://www.tpisoftware.com/contact" target="_blank" class="footer-link">業務諮詢</a>
                    <a href="https://www.tpisoftware.com" target="_blank" class="footer-link">官方網站</a>
                </div>
            </div>
        </div>
        <div class="footer-bottom">
            <p>© 2026 TPIsoftware 昕力資訊股份有限公司. All rights reserved.</p>
        </div>
    </footer>

<script>
(function () {
    var isEn = false;

    function applyLang(en) {
        var secs    = document.querySelectorAll('.section');
        var tags    = document.querySelectorAll('.section-tag');
        var titles  = document.querySelectorAll('.section-title');
        var qtexts  = document.querySelectorAll('.question-text');
        var badges  = document.querySelectorAll('.trust-badge');
        var kpoints = document.querySelectorAll('.key-point');

        /* Logo */
        document.getElementById('logo-zh').style.display = en ? 'none' : '';
        document.getElementById('logo-en').style.display = en ? ''     : 'none';

        /* Page title & lang attr */
        document.title = en ? '【英文標題】 | TPIsoftware' : '【中文標題】｜TPIsoftware';
        document.documentElement.lang = en ? 'en' : 'zh-TW';

        /* Trust badges */
        var badgeTexts = en
            ? ['【EN Badge 1】', '【EN Badge 2】', '【EN Badge 3】']
            : ['【中文標籤一】', '【中文標籤二】', '【中文標籤三】'];
        badges.forEach(function(b, i) { b.textContent = badgeTexts[i]; });

        /* Hero */
        document.querySelector('.hero-title').textContent = en ? '【EN Title】' : '【中文主標題】';

        /* Nav CTA */
        document.querySelector('.nav-cta').textContent = en ? 'Contact Us' : '聯絡我們';

        /* Section tags */
        var tagTexts = en
            ? ['【EN Tag 1】', '【EN Tag 2】']
            : ['【中文標籤一】', '【中文標籤二】'];
        tags.forEach(function(t, i) { t.textContent = tagTexts[i]; });

        /* Section titles */
        var titleTexts = en
            ? ['【EN Title 1】', '【EN Title 2】']
            : ['【中文標題一】', '【中文標題二】'];
        titles.forEach(function(t, i) { t.textContent = titleTexts[i]; });

        /* Question texts */
        var qTexts = en
            ? ['"【EN Question 1】"', '"【EN Question 2】"']
            : ['「【中文問題一】」', '「【中文問題二】」'];
        qtexts.forEach(function(q, i) { q.textContent = qTexts[i]; });

        /* Key points */
        var kpTexts = en
            ? ['【EN Key Point 1】']
            : ['【中文重點一】'];
        kpoints.forEach(function(k, i) { k.innerHTML = kpTexts[i]; });

        /* ── Section 1 ── */
        var s1bullets = en
            ? ['【EN point 1】', '【EN point 2】', '【EN point 3】']
            : ['【要點一】', '【要點二】', '【要點三】'];
        secs[0].querySelectorAll('.bullet-list li')
               .forEach(function(li, i) { li.textContent = s1bullets[i]; });

        /* ── Section 2 ── */
        var s2 = secs[1];
        s2.querySelector('h3').textContent = en ? '【EN h3】' : '【中文子標題】';

        var s2cards = s2.querySelectorAll('.card');
        if (s2cards[0]) {
            s2cards[0].querySelector('.card-title').textContent = en ? '【EN Card A】' : '【卡片標題 A】';
            var s2aLi = en ? ['【A pt1】', '【A pt2】'] : ['【A 點一】', '【A 點二】'];
            s2cards[0].querySelectorAll('li').forEach(function(li, i) { li.textContent = s2aLi[i]; });
        }
        if (s2cards[1]) {
            s2cards[1].querySelector('.card-title').textContent = en ? '【EN Card B】' : '【卡片標題 B】';
            var s2bLi = en ? ['【B pt1】', '【B pt2】'] : ['【B 點一】', '【B 點二】'];
            s2cards[1].querySelectorAll('li').forEach(function(li, i) { li.textContent = s2bLi[i]; });
        }

        /* ── CTA ── */
        var ctaEyebrow = document.querySelector('.cta-eyebrow');
        if (ctaEyebrow) ctaEyebrow.textContent = en ? '【EN Eyebrow】' : '【中文 Eyebrow】';
        var ctaTitle = document.querySelector('.cta-title');
        if (ctaTitle) ctaTitle.innerHTML = en ? '【EN CTA Title】' : '【中文 CTA 標題】';
        var ctaDesc = document.querySelector('.cta-desc');
        if (ctaDesc) ctaDesc.innerHTML = en ? '【EN CTA Desc】' : '【中文說明】';
        var ctaBtns = document.querySelectorAll('.cta-buttons a');
        if (ctaBtns[0]) ctaBtns[0].textContent = en ? 'Contact Us' : '聯絡我們';
        if (ctaBtns[1]) ctaBtns[1].textContent = en ? 'Learn More' : '了解更多';

        /* ── Footer ── */
        var ftDesc = document.querySelector('.footer-desc');
        if (ftDesc) ftDesc.textContent = en ? '【EN Desc】' : '【中文描述】';
        var ftColTitles = document.querySelectorAll('.footer-col-title');
        ['Our Services', 'Contact Us'].forEach(function(t, i) {
            if (ftColTitles[i]) ftColTitles[i].textContent = en ? t : ['服務項目', '聯絡我們'][i];
        });
        var ftLinks = document.querySelectorAll('.footer-link');
        var ftLinkTxts = en
            ? ['【EN Link 1】', '【EN Link 2】', 'Business Inquiry', 'Official Website']
            : ['【中文連結一】', '【中文連結二】', '業務諮詢', '官方網站'];
        ftLinks.forEach(function(l, i) { l.textContent = ftLinkTxts[i]; });
        var ftBottom = document.querySelector('.footer-bottom p');
        if (ftBottom) ftBottom.textContent = en
            ? '© 2026 TPIsoftware Corporation. All rights reserved.'
            : '© 2026 TPIsoftware 昕力資訊股份有限公司. All rights reserved.';
    }

    window.toggleLang = function () {
        isEn = !isEn;
        applyLang(isEn);
        document.querySelector('.lang-toggle').textContent = isEn ? '中文' : 'EN';
    };
}());
</script>

</body>
</html>
```

---

## 快速參考：元件選用建議

| 內容類型 | 建議元件 |
|---------|---------|
| 單一觀點列舉 | `bullet-list` |
| 有順序的步驟 | `numbered-steps` 或 `timeline` |
| 流程/架構圖 | `flow-diagram`（橫/縱） |
| 兩個方案對比 | `two-column` + `card-warning` + `card-success` |
| 三個面向說明 | `three-column` + `card-info` |
| 數字佐證 | `stats-grid` 或 `tg-stat-num` |
| 客戶引言 | `tg-card-main` |
| 強調重要結論 | `key-point` |
| 客戶/品牌名稱 | `brand-tag` + `logo-marquee-section` |
| 導入前後對比 | `ba-wrapper` |
| 功能比較 | `table` |
| 補充資訊框 | `card card-info` 或 `card card-emphasis` |
| 最終 Call to Action | `cta-section` |

---

*此設計系統由 TPIsoftware ChatGPT Enterprise 簡報網頁萃取，版本日期：2026-03*
