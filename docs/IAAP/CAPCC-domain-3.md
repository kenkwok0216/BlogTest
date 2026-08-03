---
sidebar_position: 5
---


# CPACC Domain 3: Standards, Laws, and Management Strategies (標準、法律與管理策略) [~20%]

Domain 3 著重於**國際標準與指引（Standards & Guidelines）**、**各國法規分類（Laws & Regulations）**，以及如何在企業或機構內部推動**無障礙組織管理（Organizational Management Strategies）**。

---

## 1. 核心標準與指引 (Standards and Guidelines)

### A. WCAG (Web Content Accessibility Guidelines - 網頁內容無障礙指引)
由 **W3C / WAI (Web Accessibility Initiative)** 制定，是全球數位無障礙的金科玉律。

* **四大核心原則 (POUR Principles)**：
  1. **Perceptible (可感知)**：資訊與使用者介面元件必須能被使用者感官所接收（如：Alt text、影片字幕、顏色對比度）。
  2. **Operable (可操作)**：介面元件與導覽必須可以被操作（如：純鍵盤可操作、給予足夠閱讀時間、避免引起癲癇的閃爍內容）。
  3. **Understandable (可理解)**：資訊與介面操作必須清晰易懂（如：語言標記、可預測的導覽結構、表單錯誤提示）。
  4. **Robust (強健性)**：內容必須具備足夠相容性，能被各種**輔助技術 (AT)** 與未來的瀏覽器穩定解析（如：語意化 HTML 標籤、正確的 ARIA 屬性）。

* **三級合規標準 (Conformance Levels)**：
  * **Level A**：最基本要求（Minimal compliance）。若未達到，部分使用者將**完全無法存取**內容。
  * **Level AA**：全球主流法律與企業標準（最常被採納的合規等級）。移除絕大多數主要障礙。
  * **Level AAA**：最高規格要求。適合特定專門網站，**不建議將全站指定為整體的法規合規目標**（因為並非所有內容都能達到 AAA）。

### B. 其他重要國際與區域標準
* **Section 508 (US)**：美國聯邦政府採購與使用資訊及通信技術（ICT）的無障礙標準（已更新採納 WCAG 2.0 AA）。
* **EN 301 549 (EU)**：歐洲 ICT 產品與服務採購無障礙標準（涵蓋 Web、App、軟體與硬體，Web 部分採納 WCAG AA）。
* **Procurement Standards (採購標準)**：利用政府/企業採購力（Purchasing Power）來要求供應商提供符合無障礙標準的產品。

---

## 2. 法律與法規類型 (Types of Laws and Regulations)

CPACC 考試強調了解**不同法規類型的立法邏輯**，而非要求硬背各國的所有法條條號：

| 法規類型 (Type of Law) | 核心概念與定義 | 代表性法規 (Examples) & 考點 |
| :--- | :--- | :--- |
| **Civil Rights / Human Rights Laws (民權/人權法)** | 將無障礙視為**基本人權**。禁止基於身心障礙的歧視，保障平等參與社會的權利。 | **ADA** (Americans with Disabilities Act - 美國殘疾人法案)、**UN CRPD** (聯合國身障權利公約)。 |
| **Procurement Laws (採購法)** | 規定**政府或公家機關**購買/使用的 ICT 產品與服務必須符合無障礙標準。利用預算引導市場規範。 | **Section 508** (美國)、**EN 301 549** (歐洲採購標準)。 |
| **Domain-Specific Laws (特定領域法)** | 針對特定產業或情境（如電信、航空、教育）所訂定的無障礙法規。 | **CVAA** (美國通訊與視訊無障礙法案)、**ACAA** (美國空中運輸無障礙法案)。 |

> 💡 **CPACC 高頻考點**：
> * **ADA Title III** 涵蓋「公共場所（Places of Public Accommodation）」，目前美國法院普遍將商業網站與 App 認定為 Title III 規範的範疇。
> * **European Accessibility Act (EAA - 歐洲無障礙法案)**：涵蓋**私營企業（Private Sector）**的許多電子商務、銀行服務與硬體終端（如 ATM、電子書），影響力極廣。

---

## 3. 組織管理策略 (Organizational Management Strategies)

如何在企業內部成功推動並維持無障礙政策（Accessibility Lifecycle & Governance）：

### A. 組織能力成熟度 (Capability Maturity Models)
評估組織在無障礙領域的成熟程度，通常分為以下階梯：
1. **Ad-hoc / Reactive (臨時/被動)**：沒有正式政策，僅在收到客戶投訴或面臨訴訟時才回應。
2. **Planned / Repeatable (有計畫/可重複)**：開始制定初步標準與流程，有部分專案執行無障礙。
3. **Defined / Integrated (已定義/全面整合)**：無障礙正式納入採購、設計、開發與測試流程，有專職人員或團隊。
4. **Managed / Measured (可管理/可衡量)**：建立關鍵績效指標（KPIs），定期監控與評估無障礙品質。
5. **Optimizing / Continuous Improvement (優化/持續改善)**：無障礙成為企業文化的一部分，主動創新並持續優化流程。

### B. 關鍵管理要素 (Key Strategic Elements)
* **Executive Champion / Leadership (高階主管支持)**：需要有高層（C-level / VP）認同並分配預算與資源，否則推動易流於形式。
* **Accessibility Policy (無障礙政策)**：明確定義合規標準（如採納 WCAG 2.1 AA）、目標時程、適用範疇與責任歸屬。
* **Procurement & Vendor Management (供應商管理)**：要求外包商提供 **VPAT (Voluntary Product Accessibility Template)**，填寫 **ACR (Accessibility Conformance Report)** 來證明其產品合規性。
* **Training and Culture (培訓與文化)**：針對不同角色（Designers, Developers, QA, PM, Content Creators）提供相應的專業培訓，並非僅交給工程師。
* **Feedback and Grievance Mechanism (反饋與申訴機制)**：網站/產品必須提供明確的 Accessibility Statement（無障礙聲明）與聯絡管道，讓使用者能回報遇到的障礙。

---

## 4. 高頻考題速記錦囊 (CPACC Domain 3 High-Yield Exam Tips)

1. **POUR 原則快速判斷**：
   * 題目考「顏色對比度不足」或「圖片沒有 Alt Text」$\rightarrow$ 屬於 **Perceptible**。
   * 題目考「純鍵盤無法聚焦」或「選單無法用 Enter 開啟」$\rightarrow$ 屬於 **Operable**。
   * 題目考「表單出錯沒有文字提示說明」或「專有名詞未標記語言屬性」$\rightarrow$ 屬於 **Understandable**。
   * 題目考「自訂 UI 元件無法被螢幕閱讀器正確辨識 Role/State」$\rightarrow$ 屬於 **Robust**。
2. **VPAT / ACR 的角色**：**VPAT** 是美國資訊產業協會提出的「範本格式」，當供應商填寫完畢說明產品無障礙程度後，產出的這份報告稱為 **ACR (Accessibility Conformance Report)**。
3. **WCAG AAA 的定位**：若考題問到「企業或政府網站應該將目標定在 WCAG 哪一個等級？」，答案是 **Level AA**。Level AAA 僅作為局部優化參考，不適合作為全站合規的強制標準。
4. **Shift Left (左移原則)**：在產品生命週期中，無障礙考量越早期納入（如需求分析、UI/UX 設計階段），修復成本越低；若到了 QA 測試或上線後才修正，成本最高。

---