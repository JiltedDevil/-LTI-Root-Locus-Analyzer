# -LTI-Root-Locus-Analyzer
A web-based Root Locus plotting tool for control systems.**(By AI Studio)**

# LTI Root Locus Designer (根軌跡設計工具)

這是一個基於網頁的線性非時變 (LTI) 控制系統分析工具。它允許使用者輸入開迴路轉移函數，繪製根軌跡圖 (Root Locus)，並根據暫態響應規格（如超越量、安定時間）即時設計控制器增益 $K$。

## 📐 數學模型 (Mathematical Model)

本工具分析的系統特徵方程式為：

$$
1 + K \cdot G(s)H(s) = 0
$$

其中開迴路轉移函數定義為：

$$
G(s)H(s) = \frac{N(s)}{D(s)} = \frac{\text{Numerator}}{\text{Denominator}}
$$

---

## 🚀 使用說明 (User Guide)

### 1. 輸入系統模型 (System Model)
請依照 **$s$ 的降冪排列** 輸入多項式係數，並用**逗號**分隔。

* **Numerator $N(s)$ (分子)**
    * 若分子為 $s + 2$，請輸入 `1, 2`
    * 若分子為常數 $1$，請輸入 `1`
* **Denominator $D(s)$ (分母)**
    * 若分母為 $s^2 + 6s + 8$，請輸入 `1, 6, 8`
    * **注意**：缺項必須補 0。例如 $s^2 + 4$，請輸入 `1, 0, 4`

### 2. 設定設計規格 (Design Specs)
透過勾選 checkbox 來顯示限制區域，檢查閉迴路極點是否滿足需求。

* **Transient Response (阻尼比 $\zeta$)**
    * 定義系統的超越量 (Percentage Overshoot, %OS)。
    * 合格區域：$\zeta \geq \zeta_{min}$ (綠色圓錐狀區域)。
    * 公式關係：
    $$
    \%OS = e^{-\frac{\zeta\pi}{\sqrt{1-\zeta^2}}} \times 100\%
    $$

* **Max Settling Time ($T_s$)**
    * 定義系統的安定時間 (Settling Time)。
    * 合格區域：實部 $\sigma \leq -4/T_s$ (垂直虛線左側)。
    * 公式關係 (2% 準則)：
    $$
    T_s \approx \frac{4}{\zeta\omega_n}
    $$

* **Min Natural Freq ($\omega_n$)**
    * 定義系統的自然頻率，影響響應速度。
    * 合格區域：原點外的半圓區域。

### 3. 調整增益 (Gain Tuning)
* **滑桿調整**：拖曳滑桿可即時觀察閉迴路極點 (Closed-Loop Poles) 在軌跡上的移動。
* **手動輸入**：若滑桿範圍不足 (系統自動計算適應性上限)，您可以直接在滑桿旁的數字框輸入更大的數值 (例如 `1000`)。

---
本工具可以使用電腦(PC)、手機、平板查看，但非常建議使用電腦，因為優化的不是很好。

---

## 🛠 技術架構
* **Core**: Vanilla JavaScript (No heavy frameworks)
* **Rendering**: Custom SVG Engine (React-based structure)
* **Math**: Custom Complex Number Arithmetic implementation

License: MIT
