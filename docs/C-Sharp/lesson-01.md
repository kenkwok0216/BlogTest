---
sidebar_position: 3
---

# 🟢 Lesson 1: 基礎資料型態與 Console 輸出

歡迎來到 C# 的第一課！在本單元中，我們將學習如何宣告最常用的 4 種**基本資料型態**，以及如何使用 `Console.WriteLine()` 將結果印在控制台上。

---

## 💻 範例程式碼

```csharp
using System;

class Program {
    static void Main() {
        // 1. 字串 (string)：儲存文字
        string test = "string";
        Console.WriteLine(test);

        // 2. 整數 (int)：儲存沒有小數點的整數
        int num = 3;
        Console.WriteLine(num);

        // 3. 浮點數 (double)：儲存帶有小數點的數字
        double number = 3.02;
        Console.WriteLine(number);

        // 4. 布林值 (bool)：儲存真 (true) 或假 (false)
        bool check1 = true;
        Console.WriteLine(check1);

        bool check2 = false;
        Console.WriteLine(check2);

        // 5. 字串串接 (String Concatenation)
        string demo = "demo";
        Console.WriteLine("demo" + 1);
    }
}
```

---

## 🖥️ 預期輸出 (Expected Output)

執行程式後，控制台 (Console) 將會顯示以下內容：

```text
string
3
3.02
True
False
demo1
```

---

## 📌 本課重點總結 (Summary)

:::note 重點摘要
1. **`Console.WriteLine()`**：用於在控制台上輸出內容，並在最後自動換行。
2. **基本資料型態 (Data Types)**：
   - **`string`**：字串，用雙引號 `""` 包裹文字內容（例如 `"string"`）。
   - **`int`**：整數，用於儲存無小數點的整數數字（例如 `3`）。
   - **`double`**：雙精度浮點數，用於儲存帶有小數點的數值（例如 `3.02`）。
   - **`bool`**：布林值，僅有 `true`（真）與 `false`（假）兩種狀態（輸出時顯示為 `True` / `False`）。
3. **字串串接 (String Concatenation)**：
   - 使用加號 `+` 可以將字串與其他資料型態（如整數）結合在一起，C# 會自動將數值轉換為字串後進行串接（例如 `"demo" + 1` 會變為 `"demo1"`）。
:::