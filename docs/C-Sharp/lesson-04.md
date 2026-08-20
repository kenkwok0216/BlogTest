---
sidebar_position: 6
---

# 🟢 Lesson 4: 關聯與邏輯運算子

在這一課中，我們將擴充比較運算子的範圍（包含大於、小於、大於等於、小於等於），並學習如何結合多個條件的**邏輯運算子**（`&&`, `||`, `!`），以及常見的字串轉整數方法 `int.Parse()`。

---

## 💻 範例程式碼

```csharp
using System;

class Program {
    static void Main() {
        // 常用的符號速查：
        // >  大於
        // <  小於
        // >= 大於或等於
        // <= 小於或等於
        // !  邏輯非 (NOT / 反相)
        // != 不等於
        // && 邏輯與 (AND / 兩者皆須成立)
        // || 邏輯或 (OR / 其中一者成立即可)
        // int.Parse() 可以將文字 (string) 轉換為整數 (int)

        Console.WriteLine(3 > 3);     // false
        Console.WriteLine(3 < 3);     // false
        
        Console.WriteLine(3 >= 3);    // true
        Console.WriteLine(!(3 >= 3)); // false (對 true 取反變成 false)

        Console.WriteLine(3 <= 3);    // true

        int test1 = 3;
        int test2 = 4;

        // 1. 邏輯與 (&&)：兩邊條件必須同時為 true 才會執行
        if(test1 == 3 && test2 == 4){
            Console.WriteLine("I am here 兩者都要正確");
        }

        // 2. 邏輯或 (||)：只要其中一邊條件為 true 即可執行
        if(test1 == 3 || test2 != 4){
            Console.WriteLine("I am here 其中一個要正確");
        }

        // 3. 邏輯等價範例 (狄摩根定律)
        // 以下兩行在邏輯上完全相同
        Console.WriteLine(!(test1 == 3 && test2 == 4)); // 輸出: False
        Console.WriteLine(test1 != 3 || test2 != 4);     // 輸出: False

        // 以下兩行在邏輯上完全相同
        Console.WriteLine(!(test1 == 3 || test2 == 4)); // 輸出: False
        Console.WriteLine(test1 != 3 && test2 != 4);     // 輸出: False
    }
}
```

---

## 🖥️ 預期輸出 (Expected Output)

執行程式後，控制台 (Console) 將會顯示以下內容：

```text
False
False
True
False
True
I am here 兩者都要正確
I am here 其中一個要正確
False
False
False
False
```

---

## 📌 本課重點總結 (Summary)

:::note 重點摘要
1. **關聯運算子**：
   - `>`、`<`、`>=`、`<=` 用於大小比較，結果皆為布林值（`true` 或 `false`）。
2. **邏輯運算子**：
   - **`&&` (AND)**：左右兩邊條件皆為 `true` 時，整體才為 `true`。
   - **`||` (OR)**：左右兩邊只要有一邊為 `true`，整體就為 `true`。
   - **`!` (NOT)**：將布林值反相（`true` 變 `false`，`false` 變 `true`）。
3. **資料轉換**：
   - **`int.Parse()`**：可用於將純數字的字串（例如 `"123"`）轉換為整數型態（`int`）。
:::