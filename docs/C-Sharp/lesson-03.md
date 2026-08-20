---
sidebar_position: 5
---

# 🟢 Lesson 3: 條件判斷 (if-else) 與比較運算子

在這一課中，我們將學習如何使用 `if-else` 進行條件判斷，並透過比較運算子（如等於、不等於）來決定程式要執行哪一段邏輯。

---

## 💻 範例程式碼

```csharp
using System;

class Program {
    static void Main() {
        int test = 3;

        // 1. 等於 (==)
        // 檢查 test 是否等於 3，成立則執行 if 內的程式碼，否則執行 else
        if(test == 3) {
            Console.WriteLine("I am here");
        } else {
            Console.WriteLine("I am not here");
        }

        // 2. 不等於 (!=)
        // 檢查 test 是否「不等於」3，不成立則會進入 else 區塊
        if(test != 3) {
            Console.WriteLine("I am not here");
        } else {
            Console.WriteLine("I am here");
        }
    }
}
```

---

## 🖥️ 預期輸出 (Expected Output)

執行程式後，控制台 (Console) 將會顯示以下內容：

```text
I am here
I am here
```

---

## 📌 本課重點總結 (Summary)

:::note 重點摘要
1. **`if-else` 條件判斷**：
   - 當 `if` 後面的條件成立（為 `true`）時，會執行 `if` 大括號內的程式碼。
   - 若條件不成立，則會轉而執行 `else` 大括號內的程式碼。
2. **比較運算子**：
   - `==` (等於)：檢查左右兩邊的值是否相等（注意是兩個等號 `=`，一個等號是賦值）。
   - `!=` (不等於)：檢查左右兩邊的值是否不相等。
:::