---
sidebar_position: 8
---

# 🟢 Lesson 7: 迴圈與控制流程綜合實戰

在這一課中，我們將透過豐富的遊戲與演算法範例（如《快打旋風 6》連段、《Minecraft》採礦、RPG 戰鬥與二元搜尋法），全面掌握 C# 的迴圈與控制流程機制。

---

## 🏋️ Q1. for 迴圈：《快打旋風 6》連段練習

**💡 核心觀念**：當你「明確知道要重複執行幾次」時，使用 `for` 迴圈是最乾淨直覺的做法。

### 💻 範例程式碼
```charp
using System;

class Program {
    static void Main() {
        Console.WriteLine("--- 🏋️ Q1. for 迴圈：《快打旋風 6》連段練習 ---");
        for (int i = 1; i <= 3; i++) {
            Console.WriteLine($"[第 {i} 次練習]: ↓ ↘ → + 輕拳 (Hadoken!)");
        }
    }
}
```

### 🖥️ 預期輸出
```text
--- 🏋️ Q1. for 迴圈：《快打旋風 6》連段練習 ---
[第 1 次練習]: ↓ ↘ → + 輕拳 (Hadoken!)
[第 2 次練習]: ↓ ↘ → + 輕拳 (Hadoken!)
[第 3 次練習]: ↓ ↘ → + 輕拳 (Hadoken!)
```
---

## ⛏️ Q2. while 迴圈：Minecraft 鎬子耐久度

**💡 核心觀念**：當你「不知道會重複幾次，只要條件成立就繼續執行」時，使用 `while` 迴圈。

### 💻 範例程式碼
```charp
using System;

class Program {
    static void Main() {
        Console.WriteLine("--- ⛏️ Q2. while 迴圈：Minecraft 鎬子耐久度 ---");
        int pickaxeDurability = 3;
        while (pickaxeDurability > 0) {
            Console.WriteLine($"敲擊方塊！木鎬剩餘耐久度: {pickaxeDurability}");
            pickaxeDurability--;
        }
        Console.WriteLine("💥 木鎬損壞了！無法繼續採礦。");
    }
}
```
### 🖥️ 預期輸出
```text
--- ⛏️ Q2. while 迴圈：Minecraft 鎬子耐久度 ---
敲擊方塊！木鎬剩餘耐久度: 3
敲擊方塊！木鎬剩餘耐久度: 2
敲擊方塊！木鎬剩餘耐久度: 1
💥 木鎬損壞了！無法繼續採礦。
```
---

## 🛑 Q3. break：找到目標物品立刻停止

**💡 核心觀念**：迴圈執行到一半，已經拿到想要的結果時，使用 `break`「立刻強制結束」迴圈。

### 💻 範例程式碼
```charp
using System;

class Program {
    static void Main() {
        Console.WriteLine("--- 🛑 Q3. break：找到目標物品立刻停止 ---");
        for (int slot = 1; slot <= 5; slot++) {
            Console.WriteLine($"正在檢查第 {slot} 格...");
            if (slot == 3) {
                Console.WriteLine("✨ 找到了關鍵物品！立刻停止搜尋。");
                break;
            }
        }
    }
}
```
### 🖥️ 預期輸出
```text
--- 🛑 Q3. break：找到目標物品立刻停止 ---
正在檢查第 1 格...
正在檢查第 2 格...
正在檢查第 3 格...
✨ 找到了關鍵物品！立刻停止搜尋。
```

---

## ⏭️ Q4. continue：跳過無價值的泥土層

**💡 核心觀念**：使用 `continue`「跳過某些不符合條件的情況」，但讓迴圈繼續執行下一輪。

### 💻 範例程式碼
```charp
using System;

class Program {
    static void Main() {
        Console.WriteLine("--- ⏭️ Q4. continue：跳過無價值的泥土層 ---");
        for (int depth = 1; depth <= 4; depth++) {
            if (depth == 2) {
                Console.WriteLine($"[第 {depth} 層是泥土]: 無價值，跳過不挖！");
                continue;
            }
            Console.WriteLine($"[第 {depth} 層是礦石]: 成功採集礦石！");
        }
    }
}
```

### 🖥️ 預期輸出
```text
--- ⏭️ Q4. continue：跳過無價值的泥土層 ---
[第 1 層是礦石]: 成功採集礦石！
[第 2 層是泥土]: 無價值，跳過不挖！
[第 3 層是礦石]: 成功採集礦石！
[第 4 層是礦石]: 成功採集礦石！
```text
---

## 🗺️ Q5. 雙重 for 迴圈：Minecraft 3x3 地圖探勘

**💡 核心觀念**：如何用雙重迴圈產生 2D 網格地圖，並使用 `continue` 排除危險座標。

### 💻 範例程式碼
```charp
using System;

class Program {
    static void Main() {
        Console.WriteLine("--- 🗺️ Q5. 雙重 for 迴圈：Minecraft 3x3 地圖探勘 ---");
        for (int x = 1; x <= 3; x++) {
            for (int z = 1; z <= 3; z++) {
                if (x == 2 && z == 2) {
                    Console.WriteLine($"   [X:{x}, Z:{z}] ⚠️ 岩漿危險區！跳過此區域。");
                    continue;
                }
                Console.WriteLine($"   [X:{x}, Z:{z}] 🗺️ 區域探勘完成。");
            }
        }
    }
}
```

### 🖥️ 預期輸出
```text
--- 🗺️ Q5. 雙重 for 迴圈：Minecraft 3x3 地圖探勘 ---
    [X:1, Z:1] 🗺️ 區域探勘完成。
    [X:1, Z:2] 🗺️ 區域探勘完成。
    [X:1, Z:3] 🗺️ 區域探勘完成。
    [X:2, Z:1] 🗺️ 區域探勘完成。
    [X:2, Z:2] ⚠️ 岩漿危險區！跳過此區域。
    [X:2, Z:3] 🗺️ 區域探勘完成。
    [X:3, Z:1] 🗺️ 區域探勘完成。
    [X:3, Z:2] 🗺️ 區域探勘完成。
    [X:3, Z:3] 🗺️ 區域探勘完成。
```
---

## ⚔️ Q6. 複雜 while 迴圈：Boss 戰回合模擬

**💡 核心觀念**：結合 `while`、`break` 與 `continue` 打造包含無敵防護罩機制的戰鬥迴圈。

### 💻 範例程式碼
```charp
using System;

class Program {
    static void Main() {
        Console.WriteLine("--- ⚔️ Q6. 複雜 while 迴圈：Boss 戰回合模擬 ---");
        int playerHP = 100;
        int bossHP = 80;
        int round = 1;

        while (playerHP > 0 && bossHP > 0) {
            Console.WriteLine($"--- 第 {round} 回合 ---");

            if (round == 3) {
                Console.WriteLine("🛡️ Boss 開啟無敵盾！本回合玩家攻擊無效。");
                playerHP -= 15;
                Console.WriteLine($"Boss 反擊！玩家剩餘血量: {playerHP}");
                round++;
                continue;
            }

            bossHP -= 30;
            playerHP -= 20;

            Console.WriteLine($"玩家施展連段！Boss 剩餘血量: {Math.Max(0, bossHP)}");
            Console.WriteLine($"Boss 反擊！玩家剩餘血量: {Math.Max(0, playerHP)}");

            if (bossHP <= 0) {
                Console.WriteLine("🎉 成功擊敗 Boss！戰鬥結束。");
                break;
            }

            round++;
        }
    }
}
```
### 🖥️ 預期輸出
```text
--- ⚔️ Q6. 複雜 while 迴圈：Boss 戰回合模擬 ---
--- 第 1 回合 ---
玩家施展連段！Boss 剩餘血量: 50
Boss 反擊！玩家剩餘血量: 80
--- 第 2 回合 ---
玩家施展連段！Boss 剩餘血量: 20
Boss 反擊！玩家剩餘血量: 60
--- 第 3 回合 ---
🛡️ Boss 開啟無敵盾！本回合玩家攻擊無效。
Boss 反擊！玩家剩餘血量: 45
--- 第 4 回合 ---
玩家施展連段！Boss 剩餘血量: 0
Boss 反擊！玩家剩餘血量: 25
🎉 成功擊敗 Boss！戰鬥結束。
```

---

## 🎯 Q7. 高難度：二元搜尋法 (Binary Search Logic)

**💡 核心觀念**：利用 `while` 迴圈實作「對半猜數字」的二元搜尋演算法，大幅提升搜尋效率。

### 💻 範例程式碼
```charp
using System;

class Program {
    static void Main() {
        Console.WriteLine("--- 🎯 Q7. 高難度：二元搜尋法 (Binary Search Logic) ---");

        int secretTarget = 42;
        int minBound = 1;
        int maxBound = 100;
        int guessCount = 0;

        while (minBound <= maxBound) {
            guessCount++;
            int currentGuess = (minBound + maxBound) / 2;

            Console.WriteLine($"[第 {guessCount} 次嘗試] 範圍 ({minBound}~{maxBound}) -> 猜測: {currentGuess}");

            if (currentGuess == secretTarget) {
                Console.WriteLine($"🎉 賓果！成功在第 {guessCount} 次猜中目標數字: {secretTarget}！");
                break;
            } else if (currentGuess < secretTarget) {
                Console.WriteLine("    👉 太小了！將下界 (minBound) 提高。");
                minBound = currentGuess + 1;
            } else {
                Console.WriteLine("    👉 太大了！將上界 (maxBound) 降低。");
                maxBound = currentGuess - 1;
            }
        }
    }
}
```

### 🖥️ 預期輸出
```text
--- 🎯 Q7. 高難度：二元搜尋法 (Binary Search Logic) ---
[第 1 次嘗試] 範圍 (1~100) -> 猜測: 50
    👉 太大了！將上界 (maxBound) 降低。
[第 2 次嘗試] 範圍 (1~49) -> 猜測: 25
    👉 太小了！將下界 (minBound) 提高。
[第 3 次嘗試] 範圍 (26~49) -> 猜測: 37
    👉 太小了！將下界 (minBound) 提高。
[第 4 次嘗試] 範圍 (38~49) -> 猜測: 43
    👉 太大了！將上界 (maxBound) 降低。
[第 5 次嘗試] 範圍 (38~42) -> 猜測: 40
    👉 太小了！將下界 (minBound) 提高。
[第 6 次嘗試] 範圍 (41~42) -> 猜測: 41
    👉 太小了！將下界 (minBound) 提高。
[第 7 次嘗試] 範圍 (42~42) -> 猜測: 42
🎉 賓果！成功在第 7 次猜中目標數字: 42！
```

---

## 💀 Q8. 毀滅級高難度：RPG 回合制 AI 狀態機與控場邏輯

**💡 核心觀念**：不使用陣列，只用「狀態標記 (Boolean Flags)」來控制複雜的 RPG 戰鬥機制（如中毒、暈眩、狂暴狀態）。

### 💻 範例程式碼
```charp
using System;

class Program {
    static void Main() {
        Console.WriteLine("--- 💀 Q8. 毀滅級高難度：RPG 回合制 AI 狀態機與控場邏輯 ---");

        int heroHP = 120;
        int bossHealth = 150;

        bool isBossStunned = false;    // 暈眩狀態 (跳過回合)
        bool isHeroPoisoned = false;   // 中毒狀態 (每回合扣血)
        bool isBossEnraged = false;    // 狂暴狀態 (傷害翻倍)

        int turnCount = 1;

        while (heroHP > 0 && bossHealth > 0) {
            Console.WriteLine($"\n=== ⚔️ 第 {turnCount} 回合 ===");

            // 1. 回合開頭：結算狀態異常 (Poison Effect)
            if (isHeroPoisoned) {
                heroHP -= 10;
                Console.WriteLine($"🤢 英雄受到毒素傷害 10 點！(剩餘 HP: {Math.Max(0, heroHP)})");
                if (heroHP <= 0) {
                    Console.WriteLine("💀 英雄毒發身亡！戰鬥結束。");
                    break;
                }
            }

            // 2. 英雄階段：每 3 回合施展一次「重擊 (Stun)」
            if (turnCount % 3 == 0) {
                bossHealth -= 35;
                isBossStunned = true;
                Console.WriteLine($"⚡ 英雄發動【雷霆重擊】！造成 35 傷害，並將 Boss 暈眩 1 回合！");
            } else {
                bossHealth -= 20;
                Console.WriteLine($"🗡️ 英雄普通攻擊，造成 20 傷害！");
            }

            // 檢查 Boss 是否被擊敗
            if (bossHealth <= 0) {
                Console.WriteLine("🎉 Boss 倒下了！英雄獲勝！");
                break;
            }

            // 3. Boss 血量檢查：低於 50 觸發狂暴模式 (Enrage State)
            if (bossHealth <= 50 && !isBossEnraged) {
                isBossEnraged = true;
                Console.WriteLine("🔥【警告】Boss 血量過低，進入狂暴狀態！攻擊力翻倍且附帶毒素！");
            }

            // 4. Boss 階段：控場與狀態判斷 (Boss Action Logic)
            if (isBossStunned) {
                Console.WriteLine("💫 Boss 處於暈眩狀態，本回合無法行動！");
                isBossStunned = false;
                turnCount++;
                continue;
            }

            // 5. Boss 攻擊算牌邏輯 (Attack Calculation)
            int bossDamage = isBossEnraged ? 30 : 15;
            heroHP -= bossDamage;
            Console.WriteLine($"👹 Boss 發動攻擊，造成 {bossDamage} 點傷害！(英雄剩餘 HP: {Math.Max(0, heroHP)})");

            if (isBossEnraged) {
                isHeroPoisoned = true;
            }

            if (heroHP <= 0) {
                Console.WriteLine("💀 英雄不敵 Boss，戰敗倒地！");
                break;
            }

            turnCount++;
        }
    }
}
```
### 🖥️ 預期輸出
```text
--- 💀 Q8. 毀滅級高難度：RPG 回合制 AI 狀態機與控場邏輯 ---

=== ⚔️ 第 1 回合 ===
🗡️ 英雄普通攻擊，造成 20 傷害！
👹 Boss 發動攻擊，造成 15 點傷害！(英雄剩餘 HP: 105)

=== ⚔️ 第 2 回合 ===
🗡️ 英雄普通攻擊，造成 20 傷害！
👹 Boss 發動攻擊，造成 15 點傷害！(英雄剩餘 HP: 90)

=== ⚔️ 第 3 回合 ===
⚡ 英雄發動【雷霆重擊】！造成 35 傷害，並將 Boss 暈眩 1 回合！
💫 Boss 處於暈眩狀態，本回合無法行動！

=== ⚔️ 第 4 回合 ===
🗡️ 英雄普通攻擊，造成 20 傷害！
🔥【警告】Boss 血量過低，進入狂暴狀態！攻擊力翻倍且附帶毒素！
👹 Boss 發動攻擊，造成 30 點傷害！(英雄剩餘 HP: 60)

=== ⚔️ 第 5 回合 ===
🤢 英雄受到毒素傷害 10 點！(剩餘 HP: 50)
🗡️ 英雄普通攻擊，造成 20 傷害！
👹 Boss 發動攻擊，造成 30 點傷害！(英雄剩餘 HP: 20)

=== ⚔️ 第 6 回合 ===
🤢 英雄受到毒素傷害 10 點！(剩餘 HP: 10)
⚡ 英雄發動【雷霆重擊】！造成 35 傷害，並將 Boss 暈眩 1 回合！
🎉 Boss 倒下了！英雄獲勝！
```
---

## 📌 本課重點總結與流程控制對照表 (Summary & Control Flow Guide)

:::note 重點摘要與控制流程功能
1. **`for` 迴圈**：
   - 適合「已知重複次數」的場景（如固定次數的連段練習）。
2. **`while` 迴圈**：
   - 適合「未知次數、依賴條件判斷」的場景（如耐久度消耗、遊戲主迴圈、二元搜尋）。
3. **`break` 指令**：
   - 用於滿足特定條件時，**立即強制終止**當前迴圈。
4. **`continue` 指令**：
   - 用於跳過當前迴圈剩餘的程式碼，**直接進入下一輪**迴圈（如過濾雜物、略過暈眩回合）。
5. **進階狀態機與演算法**：
   - 透過 Boolean Flags（布林旗標）與運算邏輯（如二元搜尋法、狀態異常結算），能夠在沒有資料結構的情況下處理高度複雜的商業與遊戲邏輯。
:::