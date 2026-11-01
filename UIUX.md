# UI/UX 設計系統與視覺規範：UniSwap 校園二手交易平台

**全國大學生二手物品交換與買賣平台 — 視覺風格、互動動線與載具適配手冊**

| 項目 | 內容 |
|---|---|
| 版本 | v2.0 |
| 設計語彙 | 學院徽章風（Collegiate）、現代 Bento Grid、Mobile-First 手機優先 |
| 核心工具 | Tailwind CSS、Lucide React、Impeccable Design Audit Engine |

---

## 1. 品牌視覺與核心概念

### 1.1 品牌識別（Collegiate Seal）
平台 Logo 採用**古典學院徽章（Academic Stamp）**風格：
- **同心同圓線條**：象徵校園循環生態圈。
- **古典鐘樓建築**：代表學術殿堂與制度化信賴。
- **交握雙手**：傳達學生彼此信任、誠實面交。
- **展開書籍與智慧型手機**：精準扣題「二手課本流通」與「數位校園市集」。

### 1.2 設計原則
1. **信賴感大於商業促銷感**：告別刺眼的螢光電商促銷紅/橘色，採用沉穩的學院藏青與溫潤象牙白。
2. **極簡無噪音（Zero Clutter）**：移除重複的搜尋框與工程除錯字樣，以資訊層次為第一優先。
3. **原生 App 觸控體驗**：嚴格落實拇指操作熱區、滑動手勢與 iOS 安全邊距（Safe Area）。

---

## 2. 色彩系統 (Color Palette)

嚴格收斂色彩，以品牌主色為骨幹，微膠囊徽章輔以低飽和重點色：

| 角色 | 色彩名稱 | HEX 代碼 | Tailwind Class | 應用場景 |
|---|---|---|---|---|
| **品牌主色** | Collegiate Navy (深學院藏青) | `#0F2942` | `bg-[#0F2942]` / `text-[#0F2942]` | Header、主標題、主要 CTA 按鈕、學院徽章 |
| **全站底色** | Warm Ivory (溫潤象牙白) | `#FAFAF9` | `bg-[#FAFAF9]` (`stone-50`) | 頁面整體底色，取代冷硬死板的純白 |
| **卡片背景** | Pure Surface (純淨卡片白) | `#FFFFFF` | `bg-white` | 商品卡片、彈窗、表單區塊，營造微層次 |
| **邊框線條** | Subtle Border (微邊框灰) | `#E7E5E4` | `border-stone-200` | 卡片邊框、分隔線，呼應 Logo 的精細線稿感 |
| **成交/安全** | Forest Green (森林墨綠) | `#059669` | `text-emerald-700` / `bg-emerald-50` | 已認證學生徽章、免費贈送標籤、交易成功狀態 |
| **交換/警示** | Warm Amber (暖琥珀色) | `#D97706` | `text-amber-700` / `bg-amber-50` | 價格強調字、以物易物標籤、預約中狀態徽章 |
| **次要文字** | Slate Muted (次要說明文字) | `#64748B` | `text-slate-500` (`stone-400`) | 學校名稱、刊登時間、次要屬性標示 |

---

## 3. 字體與排版階層 (Typography)

* **品牌與標題字體**：`font-serif` 或優雅乾淨的無襯線字體，用於 Logo 文字與重點大標題。
* **介面內文字體**：系統預設字型（Inter, -apple-system, "PingFang TC", "Microsoft JhengHei"）。

### 字級與行距規範 (8px 律動)

| 層級 | 字級 (Font Size) | 行距 (Leading) | 字重 (Weight) | 應用情境 |
|---|---|---|---|---|
| **H1** | 20px (`text-xl`) | `leading-tight` | Bold (700) | 頁面主要大標、商品詳細頁品名 |
| **H2** | 16px (`text-base`) | `leading-snug` | Bold (700) | 卡片價格、區塊標題、Modal 標題 |
| **H3** | 14px (`text-sm`) | `leading-snug` | Medium (500) | 商品卡片標題（限制 2 行，`line-clamp-2`） |
| **Body** | 13px (`text-[13px]`) | `leading-relaxed`| Normal (400) | 商品詳細描述、表單說明文案 |
| **Caption** | 11px (`text-[11px]`) | `leading-none` | Medium (500) | 微膠囊標籤（九成新、已認證、學校面交點） |

---

## 4. 載具適配與佈局結構 (Universal Layout)

### 4.1 全載具自適應外框（Responsive Wrapper）
避免在寬螢幕桌機（1920px）上卡片過度拉扯變形，採用「App Canvas 置中容器」：
```html
<!-- 桌面端自動居中並賦予精緻邊框陰影，手機端 100% 滿版無縫貼合 -->
<div className="min-h-screen bg-[#FAFAF9] flex justify-center">
  <main className="w-full max-w-md md:max-w-xl lg:max-w-2xl min-h-screen flex flex-col bg-[#FAFAF9] sm:shadow-2xl sm:border-x sm:border-stone-200">
    <!-- 頁面內容 -->
  </main>
</div>
```

### 4.2 觸控熱區與 Safe Area 防禦
- **44px 拇指法則**：所有圖示按鈕、分類膠囊、表單輸入框的最小點擊高度 `min-h-[44px]`。
- **iOS 底部安全邊距**：底部彈窗與導覽欄配置：
  `pb-[max(1rem,env(safe-area-inset-bottom))]`，防止被 iPhone Home Bar 遮蔽。

---

## 5. 核心元件視覺規範

### 5.1 頂部導覽列 (Mobile Header)
- **左側**：圓形徽章 Logo（36x36px）＋古典襯線「UniSwap 校園二手」。
- **右側**：微膠囊「+ 上架」按鈕與精簡版「身分切換下拉選單 (Role Switcher)」，徹底移除原本佔版面之四色橫條。
- **單一搜尋列**：導覽列不放重複搜尋框，全頁面僅保留中央一個帶有微陰影與圓角的外框。

### 5.2 橫向分類滑動膠囊 (Category Pills)
- 手機端支援平滑水平滾動（`overflow-x-auto no-scrollbar`）。
- 首尾使用 `-mx-4 px-4` 確保滑動至兩側時具備 16px 呼吸邊距。
- **選取狀態**：深學院藏青背景 (`bg-[#0F2942] text-white`)；**未選取**：白底微邊框 (`bg-white text-stone-600 border border-stone-200`)。

### 5.3 商品卡片 (Product Card - Bento Grid)
- **排版**：手機端雙欄（`grid-cols-2 gap-3`），平板端三欄（`sm:grid-cols-3`）。
- **圖片**：嚴格 1:1 正方形比例（`aspect-square`），圓角 `rounded-xl`。
- **浮動標籤（Micro Pill Badges）**：
  - 左上角：屋況標籤（半透明黑底白字 `bg-black/60 text-white text-[10px]`）。
  - 右下角：交易型態標籤（淡底深字 `買賣: slate` / `交換: amber` / `贈送: emerald`）。
- **標題高度防禦**：使用 `line-clamp-2 h-9`，防止卡片因字數長短不齊造成參差不齊。

### 5.4 快速預覽彈窗 (ItemQuickViewModal)
- 手機端由底部平滑彈出（Bottom Sheet 體驗）。
- 提供多角度縮圖切換、賣家信用徽章、定點面交校園標註。
- 底部固定雙 CTA 動作：【提議交換】（琥珀微邊框）與【我要購買】（藏青飽和底色）。

---

## 6. 狀態設計 (Feedback States)

1. **載入骨架 (Skeleton Screen)**：
   - 採用帶微閃爍動畫的灰質骨架卡片（`animate-pulse bg-stone-200`），取代生硬的轉圈菊花圖示。
2. **空白防禦 (Empty States)**：
   - 包含溫和的線條圖示、親切中文引導文字與「清除篩選條件」按鈕。
3. **破圖優化 (Image Fallback)**：
   - 全面配置 `onError` 備援機制，圖片載入失敗時無縫降級為預設高畫質書本/商品情境圖。