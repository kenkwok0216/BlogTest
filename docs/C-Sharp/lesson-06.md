---
sidebar_position: 8
---

# 🟢 Lesson 6: Array, List, Dictionary 與進階搜尋綜合實戰

在這一課中，我們將透過《快打旋風 6》與《Minecraft》的有趣範例，全面學習 C# 中三大核心資料結構：**Array (陣列)**、**List (清單)**、**Dictionary (字典)**，並學會使用現代的 **LINQ (.FirstOrDefault, .Where)** 與 **Lambda 運算式 (=>)** 來大幅提升開發效率。

---

## 🏢 1. Array (陣列) 與基礎搜尋實戰
* **特點**：尺寸固定，未賦值處預設為 `null`。
* **核心方法/屬性**：`.Length`, 索引存取 `[index]`, `Array.IndexOf()`。

### 💻 範例程式碼
```csharp
using System;

class Program {
    static void Main() {
        Console.WriteLine("--- 🏢 1. Array (陣列) 與基礎搜尋實戰 ---");

        // 🎮 【快打旋風 6 範例】：現代模式的 4 個固定必殺技方向鍵
        string[] sf6SpecialMoves = new string[4];
        sf6SpecialMoves[0] = "神龍拳 (單純按必殺鍵)";
        sf6SpecialMoves[1] = "波動拳 (前 + 必殺鍵)";
        sf6SpecialMoves[2] = "昇龍拳 (下 + 必殺鍵)";
        sf6SpecialMoves[3] = "龍卷旋風腳 (後 + 必殺鍵)";

        int sf6Input = 2; // 模擬玩家按下「下 + 必殺鍵」
        Console.WriteLine($"[SF6 戰鬥系統]: 隆(Ryu) 執行了技能：【{sf6SpecialMoves[sf6Input]}】！");
        
        // .Length 取得 Array (陣列) 的長度
        Console.WriteLine($"[Array 屬性展示]: 招式欄總格子數 (.Length)：{sf6SpecialMoves.Length}");

        // 🎮 【Minecraft 範例】：快捷物品欄（Hotbar）與位置搜尋 (Array.IndexOf)
        string[] mcHotbar = new string[9];
        mcHotbar[0] = "鑽石鎬";
        mcHotbar[1] = "火把";
        mcHotbar[2] = "圓石";
        mcHotbar[8] = "烤牛肉";

        int mcScroll = 0;
        Console.WriteLine($"[MC 系統]: 玩家手上目前正拿著：【{mcHotbar[mcScroll]}】準備挖礦！");

        // 檢查 null 防錯
        int emptyCheckSlot = 5;
        if (mcHotbar[emptyCheckSlot] == null){
            Console.WriteLine($"[MC 系統防錯]: 快捷列第 {emptyCheckSlot} 格是空的 (null)，可以直接放入新方塊！");
        }

        // 使用 Array.IndexOf 尋找特定道具的格子索引
        int torchIndex = Array.IndexOf(mcHotbar, "火把");
        Console.WriteLine($"[Array.IndexOf]: 「火把」位於快捷列第 {torchIndex} 格");

        int swordIndex = Array.IndexOf(mcHotbar, "下界合金劍");
        if (swordIndex == -1){
            Console.WriteLine("[Array.IndexOf]: 快捷列中沒有找到「下界合金劍」！(回傳 -1)");
        }

        // 遍歷陣列
        Console.WriteLine("[MC 系統 - 盤點快捷列]:");
        foreach(string item in mcHotbar){
            if (item != null){
                Console.WriteLine($" -> 發現道具：{item}");
            }
        }
    }
}
```

### 🖥️ 預期輸出
```text
--- 🏢 1. Array (陣列) 與基礎搜尋實戰 ---
[SF6 戰鬥系統]: 隆(Ryu) 執行了技能：【昇龍拳 (下 + 必殺鍵)】！
[Array 屬性展示]: 招式欄總格子數 (.Length)：4
[MC 系統]: 玩家手上目前正拿著：【鑽石鎬】準備挖礦！
[MC 系統防錯]: 快捷列第 5 格是空的 (null)，可以直接放入新方塊！
[Array.IndexOf]: 「火把」位於快捷列第 1 格
[Array.IndexOf]: 快捷列中沒有找到「下界合金劍」！(回傳 -1)
[MC 系統 - 盤點快捷列]:
 -> 發現道具：鑽石鎬
 -> 發現道具：火把
 -> 發現道具：圓石
 -> 發現道具：烤牛肉
```

---

## 🧾 2. List (清單) 8 大核心方法與屬性實戰
* **特點**：動態增刪，支援 Lambda 條件比對。
* **核心方法/屬性**：`.Add()`, `.Remove()`, `.RemoveAt()`, `.Count`, `.Contains()`, `.Exists()`, `.Find()`, `.FindAll()`, `.IndexOf()`。

### 💻 範例程式碼
```csharp
using System;
using System.Collections.Generic;

class Program {
    static void Main() {
        Console.WriteLine("--- 🧾 2. List (清單) 8 大核心方法與屬性實戰 ---");

        List<string> sf6ComboHistory = new List<string> { "↓", "↘", "→", "輕拳", "重拳" };

        // 1. .Add() - 新增招式到連段末端
        sf6ComboHistory.Add("EX必殺技");
        Console.WriteLine($"[1. .Add()]: 尾端追加招式後完整連段：{string.Join(" -> ", sf6ComboHistory)}");

        // 2. .Count - 取得連段總按鍵數
        Console.WriteLine($"[2. .Count]: 原始輸入按鍵總數：{sf6ComboHistory.Count} 下");

        // 3. .RemoveAt() - 精準刪除索引 4 的按鍵
        sf6ComboHistory.RemoveAt(4); // 刪除 "重拳"
        sf6ComboHistory[3] = "中拳";  // 將 "輕拳" 修正為 "中拳"
        Console.WriteLine($"[3. .RemoveAt()]: 修正後的連段指令流：{string.Join(" -> ", sf6ComboHistory)}");

        // 4. .Exists() - 使用 Lambda 檢查連段是否包含特定條件
        bool hasSpecial = sf6ComboHistory.Exists(move => move.Contains("必殺技"));
        Console.WriteLine($"[4. .Exists()]: 此連段是否包含必殺技？ {hasSpecial}");

        // 5. .Find() - 搜尋第一個符合條件的元素
        string specialInput = sf6ComboHistory.Find(move => move.Contains("必殺技"));
        Console.WriteLine($"[5. .Find()]: 找到的第一個必殺招式：【{specialInput}】");

        // 6. .FindAll() - 搜尋所有符合條件的元素，並回傳新的 List
        List<string> arrowMoves = sf6ComboHistory.FindAll(move => move == "↓" || move == "↘" || move == "→");
        Console.WriteLine($"[6. .FindAll()]: 提取連段中的所有方向鍵：{string.Join(", ", arrowMoves)}");

        // 🎮 【Minecraft 範例】：背包物資管理與消耗
        List<string> mcInventory = new List<string> { "泥土", "鐵礦石", "煤炭", "鐵礦石" };

        // 7. .Contains() - 精確檢查背包是否有特定物品
        if (mcInventory.Contains("鐵礦石")){
            // 8. .Remove() - 刪除第一個遇到的匹配項目
            mcInventory.Remove("鐵礦石");
            Console.WriteLine("[7. .Contains() & 8. .Remove()]: 成功從背包消耗一塊鐵礦石！");
        }

        Console.WriteLine($"[MC 背包]: 剩餘物品：{string.Join(", ", mcInventory)}");
        Console.WriteLine($"泥土在第 {mcInventory.IndexOf("泥土")} 格");
        Console.WriteLine($"銅礦石在第 {mcInventory.IndexOf("銅礦石")} 格 (找不到回傳 -1)");
    }
}
```

### 🖥️ 預期輸出
```text
--- 🧾 2. List (清單) 8 大核心方法與屬性實戰 ---
[1. .Add()]: 尾端追加招式後完整連段：↓ -> ↘ -> → -> 輕拳 -> 重拳 -> EX必殺技
[2. .Count]: 原始輸入按鍵總數：6 下
[3. .RemoveAt()]: 修正後的連段指令流：↓ -> ↘ -> → -> 中拳 -> EX必殺技
[4. .Exists()]: 此連段是否包含必殺技？ True
[5. .Find()]: 找到的第一個必殺招式：【EX必殺技】
[6. .FindAll()]: 提取連段中的所有方向鍵：↓, ↘, →
[7. .Contains() & 8. .Remove()]: 成功從背包消耗一塊鐵礦石！
[MC 背包]: 剩餘物品：泥土, 煤炭, 鐵礦石
泥土在第 0 格
銅礦石在第 -1 格 (找不到回傳 -1)
```

---

## 🔐 3. Dictionary (字典) 5 大核心方法與屬性實戰
* **特點**：$O(1)$ 快速存取，Key 絕不重複。
* **核心方法/屬性**：`.Add()`, `.ContainsKey()`, `.ContainsValue()`, `.TryGetValue()`, `.Count`。

### 💻 範例程式碼
```csharp
using System;
using System.Collections.Generic;

class Program {
    static void Main() {
        Console.WriteLine("--- 🔐 3. Dictionary (字典) 5 大核心方法與屬性實戰 ---");

        Dictionary<string, string> sf6DamageTable = new Dictionary<string, string>();
        sf6DamageTable.Add("普通輕拳", "300 傷害");
        sf6DamageTable.Add("真空波動拳", "3200 傷害");
        sf6DamageTable.Add("神龍烈破", "4500 傷害");

        Console.WriteLine($"[1. .Add() & 2. .Count]: 出招表已建置，目前招式數 (.Count)：{sf6DamageTable.Count} 招");

        string checkSkill = "瞬獄殺";
        if (!sf6DamageTable.ContainsKey(checkSkill)){
            Console.WriteLine($"[3. .ContainsKey()]: 出招表內沒有【{checkSkill}】，跳過查表以防止 Crash！");
        }

        Dictionary<string, int> mcBlockHardness = new Dictionary<string, int>
        {
            { "黑曜石", 50 },
            { "圓石", 2 },
            { "泥土", 1 },
            { "玻璃", 1 }
        };

        Console.WriteLine("硬度數值: " + mcBlockHardness["圓石"]);

        string searchBlock = "圓石";
        if (mcBlockHardness.TryGetValue(searchBlock, out int hardnessValue)){
            Console.WriteLine($"[4. .TryGetValue()]: 成功查到【{searchBlock}】，硬度數值為：{hardnessValue}");
        }

        if (mcBlockHardness.TryGetValue("玻璃", out int glassVal)){
            mcBlockHardness["玻璃"] = 0;
            Console.WriteLine($"玻璃更新後的硬度數值為：{mcBlockHardness["玻璃"]}");
        }

        bool hasIndestructible = mcBlockHardness.ContainsValue(-1);
        Console.WriteLine($"[5. .ContainsValue()]: 資料庫中是否有不可破壞方塊(-1)？ {hasIndestructible}");
    }
}
```

### 🖥️ 預期輸出
```text
--- 🔐 3. Dictionary (字典) 5 大核心方法與屬性實戰 ---
[1. .Add() & 2. .Count]: 出招表已建置，目前招式數 (.Count)：3 招
[3. .ContainsKey()]: 出招表內沒有【瞬獄殺】，跳過查表以防止 Crash！
硬度數值: 2
[4. .TryGetValue()]: 成功查到【圓石】，硬度數值為：2
玻璃更新後的硬度數值為：0
[5. .ContainsValue()]: 資料庫中是否有不可破壞方塊(-1)？ False
```

---

## 🚀 4. LINQ 全局高階搜尋實戰
* **特點**：語法統一，適用於 Array、List、Dictionary 等所有集合。
* **核心方法**：`.FirstOrDefault()`, `.Where()`。

### 💻 範例程式碼
```csharp
using System;
using System.Collections.Generic;
using System.Linq;

class Program {
    static void Main() {
        Console.WriteLine("--- 🚀 4. LINQ 全局高階搜尋實戰 ---");

        string[] mcHotbar = { "鑽石鎬", "火把", "圓石", null, null, null, null, null, "烤牛肉" };
        string targetBlock = "金礦石";
        string foundBlock = mcHotbar.FirstOrDefault(item => item == targetBlock);
        string foundBlockWithDefault = mcHotbar.FirstOrDefault(item => item == targetBlock, "空氣");

        Console.WriteLine($"[LINQ FirstOrDefault]: 背包未搜尋到「{targetBlock}」並傳回預設值「{foundBlockWithDefault}」！");

        if (foundBlock == null){
            Console.WriteLine($"[LINQ FirstOrDefault]: 背包未搜尋到「{targetBlock}」，安全的傳回 null 而非引發崩潰！");
        }

        Dictionary<string, int> mcBlockHardness = new Dictionary<string, int>
        {
            { "黑曜石", 50 },
            { "圓石", 2 },
            { "泥土", 1 },
            { "玻璃", 0 }
        };

        var hardBlocks = mcBlockHardness.Where(kvp => kvp.Value >= 2);
        Console.WriteLine("[LINQ Where]: 所有硬度 >= 2 的方塊：");
        foreach (var kvp in hardBlocks) {
            Console.WriteLine($" -> {kvp.Key}: 硬度 {kvp.Value}");
        }
    }
}
```

### 🖥️ 預期輸出
```text
--- 🚀 4. LINQ 全局高階搜尋實戰 ---
[LINQ FirstOrDefault]: 背包未搜尋到「金礦石」並傳回預設值「空氣」！
[LINQ FirstOrDefault]: 背包未搜尋到「金礦石」，安全的傳回 null 而非引發崩潰！
[LINQ Where]: 所有硬度 >= 2 的方塊：
 -> 黑曜石: 硬度 50
 -> 圓石: 硬度 2
```

---

## 🔄 5. 傳統迴圈與現代 Lambda 寫法對照
* **特點**：對照最傳統的 `for` (索引存取) 與現代 Lambda (如 `.ForEach`) 的實作差異。

### 💻 範例程式碼
```csharp
using System;
using System.Collections.Generic;

class Program {
    static void Main() {
        Console.WriteLine("--- 🔄 5. 傳統迴圈與現代 Lambda 寫法對照 ---");

        List<string> sf6ComboHistory = new List<string> { "↓", "↘", "→", "中拳", "EX必殺技" };

        // 傳統 for 迴圈走訪
        Console.WriteLine("[傳統 for 迴圈]:");
        for (int i = 0; i < sf6ComboHistory.Count; i++){
            Console.WriteLine($" -> 按鍵 [{i}]: {sf6ComboHistory[i]}");
        }

        // 現代 Lambda 走訪
        Console.WriteLine("[現代 List.ForEach + Lambda]:");
        sf6ComboHistory.ForEach(move => Console.WriteLine($" -> [SF6] => {move}"));
    }
}
```

### 🖥️ 預期輸出
```text
--- 🔄 5. 傳統迴圈與現代 Lambda 寫法對照 ---
[傳統 for 迴圈]:
 -> 按鍵 [0]: ↓
 -> 按鍵 [1]: ↘
 -> 按鍵 [2]: →
 -> 按鍵 [3]: 中拳
 -> 按鍵 [4]: EX必殺技
[現代 List.ForEach + Lambda]:
 -> [SF6] => ↓
 -> [SF6] => ↘
 -> [SF6] => →
 -> [SF6] => 中拳
 -> [SF6] => EX必殺技
```

---

## 📌 本課重點總結 (Summary)

:::note 重點摘要與方法功能
1. **Array (陣列) 核心與方法**：
   * 尺寸固定，建立時必須指定大小（例如 `new string[4]`）。
   * **`.Length`**：取得陣列的總格子數（長度）。
   * **`Array.IndexOf(array, value)`**：搜尋特定元素在陣列中的索引位置，若找不到則回傳 `-1`。

2. **List (清單) 8 大核心方法與屬性**：
   * 可變動長度的動態集合。
   * **`.Add(item)`**：將新元素新增到清單的尾端。
   * **`.Count`**：取得清單目前的元素總數量。
   * **`.RemoveAt(index)`**：精準刪除指定索引位置的元素。
   * **`.Exists(predicate)`**：使用 Lambda 條件檢查清單中是否存在符合的元素（回傳布林值 `true`/`false`）。
   * **`.Find(predicate)`**：尋找並回傳第一個符合 Lambda 條件的元素。
   * **`.FindAll(predicate)`**：尋找所有符合 Lambda 條件的元素，並組成一個新的 List 回傳。
   * **`.Contains(item)`**：檢查清單是否精準包含某個特定元素。
   * **`.Remove(item)`**：刪除清單中第一個遇到的匹配元素。

3. **Dictionary (字典) 核心方法與屬性**：
   * 以 `Key-Value`（鍵值對）儲存，具備 $O(1)$ 的極佳查表效能。
   * **`.Add(key, value)`**：新增一筆鍵值對資料。
   * **`.Count`**：取得字典中的鍵值對總數量。
   * **`.ContainsKey(key)`**：檢查字典中是否存在指定的 Key（用來防止因 Key 不存在而導致程式 Crash）。
   * **`.TryGetValue(key, out value)`**：一次完成「是否存在檢查」與「安全取值」，最推薦的安全查表寫法。
   * **`.ContainsValue(value)`**：檢查字典中是否有包含特定的 Value 數值。

4. **LINQ 與 Lambda 運算式 (`=>`)**：
   * **`.FirstOrDefault(predicate)`**：跨集合安全搜尋，找不到時可回傳 `null` 或自訂預設值，不會引發 Exception。
   * **`.Where(predicate)`**：根據條件過濾集合中符合的所有條目，非常適合搭配 `foreach` 進行高階篩選。
:::