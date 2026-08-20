---
sidebar_position: 10
---

# 📚 Lesson 8: N 維陣列與空間演算法完整分段筆記

---

## 🟢 Case 1: 一維陣列 (1D Array) — Minecraft 裝備欄

### 💡 核心觀念
一維陣列就像「一排有編號的置物櫃」，透過單一索引 `[Index]`（從 0 開始）來存取與修改資料。

### 💻 程式碼範例
```charp
    string[] hotbar = new string[5] { "鐵劍", "弓箭", "火把", "麵包", "空" };
    Console.WriteLine($"目前快捷列第 0 格裝備：{hotbar[0]}");
    hotbar[4] = "水桶";
    Console.WriteLine($"更新後第 4 格裝備：{hotbar[4]}");
```

### 🖥️ 預期輸出
```text
    目前快捷列第 0 格裝備：鐵劍
    更新後第 4 格裝備：水桶
```

---

## 🟢 Case 2: 二維陣列 (2D Array) — 井字遊戲棋盤

### 💡 核心觀念
二維陣列 `[,]` 就像「網格地圖 / 試算表」，使用 `[列, 行]` (`Row, Column`) 或 `[X, Y]` 座標來進行定位與渲染。

### 💻 程式碼範例
```charp
    char[,] board = new char[3, 3] {
        { 'X', 'O', ' ' },
        { ' ', 'X', 'O' },
        { ' ', ' ', 'X' }
    };
    for (int row = 0; row < 3; row++) {
        for (int col = 0; col < 3; col++) {
            Console.Write($" {board[row, col]} ");
            if (col < 2) Console.Write("|");
        }
        Console.WriteLine();
        if (row < 2) Console.WriteLine("-----------");
    }
```

### 🖥️ 預期輸出
```text
     X | O |   
    -----------
       | X | O 
    -----------
       |   | X 
```

---

## 🟢 Case 3: 交錯陣列 (Jagged Array) — 不同等級背包

### 💡 核心觀念
交錯陣列 `[][]` 是「陣列中的陣列」。每一列的長度可以不同，非常適合儲存不規則長度的資料。

### 💻 程式碼範例
```charp
    string[][] playerBag = new string[3][];
    playerBag[0] = new string[] { "小紅藥水", "木劍" };
    playerBag[1] = new string[] { "中紅藥水", "鐵劍", "盾牌", "皮甲" };
    playerBag[2] = new string[] { "大紅藥水", "鑽石劍", "金蘋果" };

    for (int lvl = 0; lvl < playerBag.Length; lvl++) {
        Console.WriteLine($"等級 {lvl + 1} 背包（共 {playerBag[lvl].Length} 格）：{string.Join(", ", playerBag[lvl])}");
    }
```

### 🖥️ 預期輸出
```text
    等級 1 背包（共 2 格）：小紅藥水, 木劍
    等級 2 背包（共 4 格）：中紅藥水, 鐵劍, 盾牌, 皮甲
    等級 3 背包（共 3 格）：大紅藥水, 鑽石劍, 金蘋果
```

---

## 🟡 Case 4: 三維陣列 (3D Array) — Minecraft 3D 立體方塊世界

### 💡 核心觀念
三維陣列 `[,,]` 可以想像成「一棟立體大樓」或「3D 體積空間」，定位點為 `[Y, X, Z]`（高度、東西、南北）。

### 💻 程式碼範例
```charp
    string[,,] voxelWorld = new string[2, 2, 2] {
        { { "泥土", "泥土" }, { "泥土", "基岩" } },
        { { "空氣", "空氣" }, { "樹葉", "空氣" } }
    };
    for (int x = 0; x < 2; x++)
        for (int z = 0; z < 2; z++)
            Console.WriteLine($"座標 [X:{x}, Y:0, Z:{z}] : {voxelWorld[0, x, z]}");
```

### 🖥️ 預期輸出
```text
    座標 [X:0, Y:0, Z:0] : 泥土
    座標 [X:0, Y:0, Z:1] : 泥土
    座標 [X:1, Y:0, Z:0] : 泥土
    座標 [X:1, Y:0, Z:1] : 基岩
```

---

## 🟡 Case 5: 動態邊界檢測 — 活用 GetLength()

### 💡 核心觀念
千萬不要在迴圈中寫死數字！應使用 `array.GetLength(dimension)` 動態取得維度長度，確保程式碼具備防呆與擴充性。

### 💻 程式碼範例
```charp
    int[,] dungeonMap = new int[2, 4] {
        { 0, 1, 0, 9 },
        { 1, 0, 0, 0 }
    };
    int rows = dungeonMap.GetLength(0);
    int cols = dungeonMap.GetLength(1);
    Console.WriteLine($"地圖尺寸：{rows} 行 x {cols} 列");
    for (int r = 0; r < rows; r++) {
        for (int c = 0; c < cols; c++) {
            if (dungeonMap[r, c] == 9)
                Console.WriteLine($"🎯 在位置 [{r}, {c}] 找到了出口！");
        }
    }
```

### 🖥️ 預期輸出
```text
    地圖尺寸：2 行 x 4 列
    🎯 地圖尺寸：2 行 x 4 列
    🎯 在位置 [0, 3] 找到了出口！
```

---

## 🔴 Case 6: 四維陣列 (4D Array) — 多重宇宙雷達掃描

### 💡 核心觀念
處理多重平行宇宙或超高維度狀態時，使用 4 維陣列 `[,,,]`，結構代表 `[Universe, Level, X, Y]`。

### 💻 程式碼範例
```charp
    int[,,,] multiverse = new int[2, 2, 3, 3];
    multiverse[0, 1, 2, 2] = 8;
    Console.WriteLine($"✨ 成功定位寶箱！[宇宙 0 | 地下層 1 | 座標 (2, 2)]");
```

### 🖥️ 預期輸出
```text
    ✨ 成功定位寶箱！[宇宙 0 | 地下層 1 | 座標 (2, 2)]
```

---

## 🔴 Case 7: 空間演算法 — 九宮格邊界安全爆炸判定

### 💡 核心觀念
計算範圍傷害（如爆炸）時，透過偏移量 `(-1, 0, 1)` 搭配 **Guard Clause（邊界安全防護檢查）**，防止超出陣列索引崩潰。

### 💻 程式碼範例
```charp
    int[,] gridMap = new int[5, 5];
    int bombX = 0, bombY = 0;
    for (int offsetX = -1; offsetX <= 1; offsetX++) {
        for (int offsetY = -1; offsetY <= 1; offsetY++) {
            int targetX = bombX + offsetX;
            int targetY = bombY + offsetY;
            if (targetX >= 0 && targetX < gridMap.GetLength(0) && targetY >= 0 && targetY < gridMap.GetLength(1)) {
                Console.WriteLine($"  💥 爆炸波及座標 [{targetX}, {targetY}]！");
            }
        }
    }
````

### 🖥️ 預期輸出
```text
      💥 爆炸波及座標 [0, 0]！
      💥 爆炸波及座標 [0, 1]！
      💥 爆炸波及座標 [1, 0]！
      💥 爆炸波及座標 [1, 1]！
```

---

## 🔴 Case 8: 迴圈存取順序效能測試 (Cache Locality)

### 💡 程式碼範例
```charp
    Stopwatch sw = new Stopwatch();
    long sum = 0;

    // 1. 2D 陣列測試 [i, j] vs [j, i]
    int size2D = 10000;
    int[,] array2D = new int[size2D, size2D];
    
    sw.Restart();
    for (int i = 0; i < size2D; i++) {
        for (int j = 0; j < size2D; j++) {
            sum += array2D[i, j];
        }
    }
    sw.Stop();
    long time2DSeq = sw.ElapsedMilliseconds;

    sum = 0;
    sw.Restart();
    for (int i = 0; i < size2D; i++) {
        for (int j = 0; j < size2D; j++) {
            sum += array2D[j, i];
        }
    }
    sw.Stop();
    long time2DStrided = sw.ElapsedMilliseconds;

    // 2. 3D 陣列測試 [i, j, k] vs [k, j, i]
    int size3D = 500;
    int[,,] array3D = new int[size3D, size3D, size3D];
    
    sum = 0;
    sw.Restart();
    for (int i = 0; i < size3D; i++) {
        for (int j = 0; j < size3D; j++) {
            for (int k = 0; k < size3D; k++) {
                sum += array3D[i, j, k];
            }
        }
    }
    sw.Stop();
    long time3DSeq = sw.ElapsedMilliseconds;

    sum = 0;
    sw.Restart();
    for (int i = 0; i < size3D; i++) {
        for (int j = 0; j < size3D; j++) {
            for (int k = 0; k < size3D; k++) {
                sum += array3D[k, j, i];
            }
        }
    }
    sw.Stop();
    long time3DStrided = sw.ElapsedMilliseconds;

    // 3. 4D 陣列測試 [i, j, k, l] vs [l, k, j, i]
    int size4D = 100;
    int[,,,] array4D = new int[size4D, size4D, size4D, size4D];
    
    sum = 0;
    sw.Restart();
    for (int i = 0; i < size4D; i++) {
        for (int j = 0; j < size4D; j++) {
            for (int k = 0; k < size4D; k++) {
                for (int l = 0; l < size4D; l++) {
                    sum += array4D[i, j, k, l];
                }
            }
        }
    }
    sw.Stop();
    long time4DSeq = sw.ElapsedMilliseconds;

    sum = 0;
    sw.Restart();
    for (int i = 0; i < size4D; i++) {
        for (int j = 0; j < size4D; j++) {
            for (int k = 0; k < size4D; k++) {
                for (int l = 0; l < size4D; l++) {
                    sum += array4D[l, k, j, i];
                }
            }
        }
    }
    sw.Stop();
    long time4DStrided = sw.ElapsedMilliseconds;
```

### 🖥️ 預期輸出
```text
    --- [2D 陣列測試: 10,000 x 10,000] ---
    ✅ 順序存取 [i, j]: 488 ms
    ❌ 跳躍存取 [j, i]: 625 ms
    ⚡ 順序存取快了: 1.28 倍

    --- [3D 陣列測試: 500 x 500 x 500] ---
    ✅ 順序存取 [i, j, k]: 408 ms
    ❌ 跳躍存取 [k, j, i]: 625 ms
    ⚡ 順序存取快了: 1.53 倍

    --- [4D 陣列測試: 100 x 100 x 100 x 100] ---
    ✅ 順序存取 [i, j, k, l]: 408 ms
    ❌ 跳躍存取 [l, k, j, i]: 1276 ms
    ⚡ 順序存取快了: 3.30 倍
```

### 📋 Case 8 重點摘要 (Summaries)
* **記憶體連續性 (Cache Locality)**：電腦的記憶體在底層是「一維線性」排列的。多維陣列在實體記憶體中也是依序攤平存放的。
* **順序存取優勢**：當使用對應順序（如 2D 的 `[i, j]` 或 4D 的 `[i, j, k, l]`）讀取時，CPU 的快取 (Cache) 能預先載入鄰近資料，大幅減少記憶體延遲。
* **跳躍存取效能損耗**：當反向或跳躍存取（如 `[l, k, j, i]`）時，會頻繁發生快取未命中 (Cache Misses)，導致效能顯著下降（在 4D 測試中甚至慢了 3.3 倍以上）。
* **實務開發建議**：編寫遊戲迴圈或高效能演算法掃描多維網格時，務必確保迴圈變數的巢狀順序與陣列宣告維度一致。