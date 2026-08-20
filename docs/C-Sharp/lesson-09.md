---
sidebar_position: 11
---

# 📚 Lesson 9: 方法與函式 (Method & Function) 完整實戰指南

這份筆記涵蓋了 C# 方法的基礎觀念、參數傳遞機制、方法多載、遊戲實戰模組，以及遞迴與迴圈的效能權衡分析。

---

## 🟢 Part 1: 基礎方法與傳回值 (Basic Methods & Return Values)

### 💡 核心觀念
* **DRY 原則 (Don't Repeat Yourself)**：方法將重複的邏輯封裝起來，避免程式碼重複。
* **`void` vs 傳回型態**：`void` 代表不回傳任何結果；若指定型態（如 `int`、`string`），則必須使用 `return` 回傳對應的值。

### 💻 程式碼範例
```charp
    using System;

    class Program {
        static void Main() {
            SayHello("Alice");

            int sumResult = Add(15, 27);
            Console.WriteLine($"15 + 27 = {sumResult}");
        }

        static void SayHello(string name) {
            Console.WriteLine($"👋 哈囉, {name}！歡迎來到 C# 方法的世界。");
        }

        static int Add(int a, int b) {
            return a + b;
        }
    }
```
### 🖥️ 預期輸出
```text
    👋 哈囉, Alice！歡迎來到 C# 方法的世界。
    15 + 27 = 42
```

---

## 🟡 Part 2: 參數傳遞機制 (Value vs ref vs out)

### 💡 核心觀念
* **Value (預設)**：傳入變數的「副本」，方法內部的修改完全不影響外部變數。
* **`ref` (傳址)**：傳入變數的記憶體位址，外部變數**必須先初始化**，方法內部修改會同步影響外部。
* **`out` (輸出參數)**：強制方法內部必須賦值，常用於安全解析（如 `TryParse`）或一次回傳多個值。

### 💻 程式碼範例
```charp
    using System;

    class Program {
        static void Main() {
            int a = 10;
            Console.WriteLine($"[Value] 呼叫前: a = {a}");
            SquareByValue(a);
            Console.WriteLine($"[Value] 呼叫後: a = {a} (原本的變數完全不受影響！)\n");

            int b = 10;
            Console.WriteLine($"[ref]   呼叫前: b = {b}");
            SquareByRef(ref b);
            Console.WriteLine($"[ref]   呼叫後: b = {b} (原本的變數直接被修改！)\n");

            if (TryParseScore("95", out int score)) {
                Console.WriteLine($"[out]   解析分數成功: {score} 分");
            }
        }

        static void SquareByValue(int number) {
            number = number * number;
            Console.WriteLine($"    --> 方法內部計算結果 number = {number}");
        }

        static void SquareByRef(ref int number) {
            number = number * number;
            Console.WriteLine($"    --> 方法內部計算結果 number = {number}");
        }

        static bool TryParseScore(string input, out int result) {
            return int.TryParse(input, out result);
        }
    }
```

### 🖥️ 預期輸出
```text
    [Value] 呼叫前: a = 10
        --> 方法內部計算結果 number = 100
    [Value] 呼叫後: a = 10 (原本的變數完全不受影響！)

    [ref]   呼叫前: b = 10
        --> 方法內部計算結果 number = 100
    [ref]   呼叫後: b = 100 (原本的變數直接被修改！)

    [out]   解析分數成功: 95 分
```

---

## 🔵 Part 3: 方法多載 (Method Overloading)

### 💡 核心觀念
* **方法多載**：允許在同一個類別中存在多個**同名方法**，但其「參數數量」或「參數型態」必須不同。
* 編譯器會根據呼叫時傳入的引數（Arguments）自動選擇對應的版本。

### 💻 程式碼範例
```charp
    using System;

    class Program {
        static void Main() {
            Console.WriteLine(FormatOutput(1250000));
            Console.WriteLine(FormatOutput(0.8524));
            Console.WriteLine(FormatOutput(true));

            Console.WriteLine(CalculateArea(5.0));
            Console.WriteLine(CalculateArea(4.0, 6.0));
            Console.WriteLine(CalculateArea("圓形", 3.0));
        }

        static string FormatOutput(int amount) => $"💰 帳戶餘額: NT$ {amount:N0}";
        static string FormatOutput(double rate) => $"📊 完成進度: {rate:P1}";
        static string FormatOutput(bool isOnline) => isOnline ? "🟢 系統狀態: 連線中" : "🔴 系統狀態: 已離線";

        static string CalculateArea(double side) => $"正方形 (邊長 {side}) 的面積為: {side * side}";
        static string CalculateArea(double width, double height) => $"矩形 ({width} x {height}) 的面積為: {width * height}";
        static string CalculateArea(string shapeName, double radius) => $"{shapeName} (半徑 {radius}) 的面積為: {Math.PI * radius * radius:F2}";
    }
```
### 🖥️ 預期輸出
```text
    💰 帳戶餘額: NT$ 1,250,000
    📊 完成進度: 85.2%
    🟢 系統狀態: 連線中
    正方形 (邊長 5) 的面積為: 25
    矩形 (4 x 6) 的面積為: 24
    圓形 (半徑 3) 的面積為: 28.27
```

---

## 🔴 Part 4: 實戰專案 - 數字鍵盤 2D 井字遊戲

### 💡 核心觀念
透過方法模組化，將遊戲的初始化、畫面渲染（Render）與狀態邏輯拆分，提升程式碼的維護性。

### 💻 程式碼範例
```charp
    using System;

    class Program {
        static void Main() {
            RunTicTacToeGame();
        }

        static void RunTicTacToeGame() {
            Console.WriteLine("--- ❌⭕ 數字鍵盤 2D 井字遊戲 (Tic-Tac-Toe) ---");
            char[,] tttBoard = new char[3, 3] {
                { ' ', ' ', ' ' },
                { ' ', ' ', ' ' },
                { ' ', ' ', ' ' }
            };
            char currentPlayer = 'X';
            RenderBoard(tttBoard, currentPlayer);
        }

        static void RenderBoard(char[,] board, char player) {
            Console.WriteLine($"\n目前玩家: {player}");
            Console.WriteLine($" {board[0, 0]} | {board[0, 1]} | {board[0, 2]} ");
            Console.WriteLine("-----------");
            Console.WriteLine($" {board[1, 0]} | {board[1, 1]} | {board[1, 2]} ");
            Console.WriteLine("-----------");
            Console.WriteLine($" {board[2, 0]} | {board[2, 1]} | {board[2, 2]} ");
        }
    }
```
### 🖥️ 預期輸出
```text
    --- ❌⭕ 數字鍵盤 2D 井字遊戲 (Tic-Tac-Toe) ---

    目前玩家: X
       |   |   
    -----------
       |   |   
    -----------
       |   |   
```
---

## 🟣 Part 5: 遞迴方法與效能權衡 (Recursion & Iteration)

### 💡 核心觀念
1. **遞迴 (Recursion)**：方法自己呼叫自己，**必須設定明確的終止條件 (Base Case)**，否則會造成堆疊溢位 (`StackOverflowException`)。
2. **遞迴 vs 迴圈權衡**：
   * **可讀性**：處理樹狀結構（如技能樹、合成配方）時，遞迴極為直覺。
   * **記憶體安全**：遞迴依賴 Call Stack，容易溢出；迴圈資料存放於 Heap，容量較大且安全。
   * **效能**：迴圈執行速度較快，沒有函式壓棧的額外開銷（Overhead）。

### 💻 程式碼範例
```charp
    using System;

    class Program {
        static void Main() {
            // 1. 基礎遞迴：倒數計時
            Countdown(3);

            // 2. 數值分解：階乘計算
            int factorialResult = Factorial(5);
            Console.WriteLine($"🎲 5! (5的階乘) = {factorialResult}\n");

            // 3. 樹狀合成配方解析
            string targetItem = "聖光長劍";
            int totalOre = GetRequiredMaterials(targetItem);
            Console.WriteLine($"\n⛏️ 總結：合成 [{targetItem}] 總共需要 {totalOre} 個基礎 [鐵礦石]");
        }

        static void Countdown(int number) {
            if (number <= 0) {
                Console.WriteLine("💥 發射！(觸發終止條件 Base Case)\n");
                return;
            }
            Console.WriteLine($"⏳ 倒數: {number}");
            Countdown(number - 1);
        }

        static int Factorial(int n) {
            if (n <= 1) return 1;
            return n * Factorial(n - 1);
        }

        static int GetRequiredMaterials(string itemName, int depth = 0) {
            string indent = new string(' ', depth * 2);
            Console.WriteLine($"{indent}🔍 正在解析 [{itemName}] 的合成配方...");

            if (itemName == "鐵礦石") {
                Console.WriteLine($"{indent}  ⛏️ [鐵礦石] 為基礎原料！");
                return 1;
            }

            if (itemName == "聖光長劍") {
                return GetRequiredMaterials("精鍛鋼", depth + 1) + GetRequiredMaterials("聖光寶石", depth + 1);
            } else if (itemName == "精鍛鋼") {
                return GetRequiredMaterials("鐵礦石", depth + 1) + GetRequiredMaterials("鐵礦石", depth + 1);
            } else if (itemName == "聖光寶石") {
                return GetRequiredMaterials("鐵礦石", depth + 1);
            }

            return 0;
        }
    }
```
### 🖥️ 預期輸出
```text
    ⏳ 倒數: 3
    ⏳ 倒數: 2
    ⏳ 倒數: 1
    💥 發射！(觸發終止條件 Base Case)

    🎲 5! (5的階乘) = 120

    🔍 正在解析 [聖光長劍] 的合成配方...
      🔍 正在解析 [精鍛鋼] 的合成配方...
        🔍 正在解析 [鐵礦石] 的合成配方...
          ⛏️ [鐵礦石] 為基礎原料！
        🔍 正在解析 [鐵礦石] 的合成配方...
          ⛏️ [鐵礦石] 為基礎原料！
      🔍 正在解析 [聖光寶石] 的合成配方...
        🔍 正在解析 [鐵礦石] 的合成配方...
          ⛏️ [鐵礦石] 為基礎原料！

    ⛏️ 總結：合成 [聖光長劍] 總共需要 3 個基礎 [鐵礦石]
```

### 📋 Part 5 重點摘要
* **遞迴核心**：必須具備明確的 **Base Case（終止條件）**，否則會發生 `StackOverflowException`。
* **適用場景**：極適合處理樹狀結構（如裝備合成、目錄樹）。
* **實務建議**：理論上所有遞迴皆可改寫為迴圈；實務上為了效能與記憶體安全，通常優先考慮迴圈（Iteration）。