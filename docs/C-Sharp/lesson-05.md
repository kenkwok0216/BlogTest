---
sidebar_position: 7
---

# 🟢 Lesson 5: 迴圈 (while 與 for) 與控制指令

在這一課中，我們將學習如何使用迴圈（`while` 與 `for`）來重複執行程式碼，並透過 `continue` 和 `break` 控制迴圈的流程，最後了解巢狀迴圈與 `do-while` 的觀念。

---

## 💻 範例程式碼與預期輸出

### 1. while 迴圈範例
```csharp
int test = 0;
while(test < 3){
    Console.WriteLine(test);
    test++;
}
```
**預期輸出：**
```text
0
1
2
```

---

### 2. for 迴圈範例（與上面的 while 效果相同）
```csharp
for(int i = 0; i < 3; i++){
    Console.WriteLine(i);
}
```
**預期輸出：**
```text
0
1
2
```

---

### 3. 巢狀迴圈 (Nested Loops)
```csharp
// for 迴圈版本：在多層迴圈下比較方便
for (int row = 0; row < 4; row++) {
    for (int col = 0; col < 5; col++) {
        Console.WriteLine(row + " , " + col);
    }
}

// 巢狀迴圈的 while 版本
int outer = 0;
while (outer < 4) {
    int inner = 0;
    while (inner < 5) {
        Console.WriteLine(outer + " , " + inner);
        inner++;
    }
    outer++;
}
```
**預期輸出：**
```text
0 , 0
0 , 1
0 , 2
0 , 3
0 , 4
1 , 0
1 , 1
1 , 2
1 , 3
1 , 4
2 , 0
2 , 1
2 , 2
2 , 3
2 , 4
3 , 0
3 , 1
3 , 2
3 , 3
3 , 4
(while 版本的輸出結果與上述相同)
```

---

### 4. continue 控制指令
```csharp
for(int i = 0; i < 10; i++){
    if(i == 2){
        continue;
    }
    Console.Write(i + " ");
}
Console.WriteLine();
```
**預期輸出：**
```text
0 1 3 4 5 6 7 8 9 
```

---

### 5. break 控制指令
```csharp
for(int i = 0; i < 10; i++){
    if(i == 2){
        break;
    }
    Console.Write(i + " ");
}
Console.WriteLine();
```
**預期輸出：**
```text
0 1 
```

---

### 6. 課外知識 (do-while)
```csharp
// 先判斷 (test1 < 3) 才進入 while 迴圈
int test1 = 0;
while(test1 < 3){
    Console.WriteLine(test1);
    test1++;
}

// 先進入 do 區塊執行一次，才判斷 (test2 < 3)
int test2 = 0;
do {
    Console.WriteLine(test2);
    test2++;
} while(test2 < 3);
```
**預期輸出：**
```text
0
1
2
0
1
2
```

---

## 📌 本課重點總結 (Summary)

:::note 重點摘要
1. **`while` 與 `for` 迴圈**：
   - `while` 適合用於條件控制次數不明確或依賴特定條件的場景。
   - `for` 將初始值、條件、遞增寫在同一行，非常適合固定次數的迴圈（例如計數器、巢狀迴圈）。
2. **巢狀迴圈 (Nested Loops)**：
   - 可以用在二維表格、矩陣或座標（如 `row` 與 `col`）的走訪。
3. **控制指令 (`continue` 與 `break`)**：
   - `continue`：略過當前迴圈剩下的一行，直接跳到下一次循環。
   - `break`：立刻終止並跳出當前迴圈。
4. **`do-while` 迴圈 (進階補充)**：
   - `while` 是「先判斷後執行」（可能一次都不執行）。
   - `do-while` 則是「先執行一次，再判斷是否繼續」（保證至少會執行一次）。
:::