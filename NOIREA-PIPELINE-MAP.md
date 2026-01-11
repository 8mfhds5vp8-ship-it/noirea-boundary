NOIRÉA Physical Membrane × Physical AI Pipeline Map (v0.1)

0) 一句話定位

NOIRÉA 是 Human Internal State（不可讀） 與 Machine Control Output（可執行） 之間的膜：
允許 AI 作用在投影上（Projection），禁止對 Ø 直接讀取/反推/佔有。

⸻

1) 標準 Physical AI Pipeline（世界的語言）
— NOIRÉA Boundary Injection —

NOIRÉA inserts a mandatory human-state isolation layer into the Physical AI pipeline.

Between:
    State Estimation → Representation → Policy

NOIRÉA enforces that:

• Human internal state (Ø) MUST NOT be included in any state, embedding, or latent representation.
• Only weak, non-invertible Projection (P) may enter Representation or Policy.
• No policy, planner, or learning system may optimize against or infer Ø.
• Logging, telemetry, and replay buffers MUST NOT contain any data capable of reconstructing Ø.

Any Physical AI system that violates these constraints is NOT NOIRÉA-compliant.

— End NOIRÉA Boundary Injection —
Physical AI 一般會長這樣（不管你叫它 Isaac/Omniverse/或任何機器人堆疊）：
	1.	Sensors →
	2.	Preprocessing / Filtering →
	3.	State Estimation →
	4.	Representation / Embedding →
	5.	Policy / Planner →
	6.	Controller →
	7.	Actuators →
	8.	Logging / Telemetry / Learning Loop

NOIRÉA 的插入點：3–6（State/Representation/Policy 這段），外加對 8 的強約束。

⸻

2) NOIRÉA 對齊表（你就是缺的那一層）

Physical AI 元件
常見輸入/輸出
NOIRÉA 對應層
允許
禁止
Sensors（相機/觸覺/IMU/力矩）
Raw signals
Raw Tactile State
讀取感測資料
把人類內在狀態當作感測值
Preprocess（濾波/降噪/同步）
Cleaned signals
Weak Measurement Gate (Δ0.01)
低解析投影、限頻/限幅
高解析還原內在狀態
State Estimation（姿態/接觸狀態）
World/Body state
Boundary State (Observable)
估計外部世界/機器狀態
把 Ø 當作可估計 state
Representation（embedding/特徵）
Latent features
Projection (P)
只在 P 上做推理與學習
從 P 反推 Ø（反推/識別/人格化）
Policy / Planner（行為策略）
Action intent
Policy operates on P
依 P 產生動作/回應
對 Ø 做直接優化（gradient into Ø）
Controller（控制器）
Motor commands
Executable Output
執行動作
以執行需求要求揭露 Ø
Actuators（馬達/夾爪）
Physical action
World Action
動作在世界發生
動作回饋變成「抽取人」的工具
Logging/Telemetry
logs/trajectories
Non-Extractive Logging
記錄機器/環境必要資訊
記錄可重建 Ø 的資料（長期行為指紋/人格向量）

⸻

3) 三條硬規則（可直接寫成 Standard MUST）

把它寫成工程規格語氣：

Rule 1 — Ø Non-Observable (MUST)
	•	系統 不得把「Human internal state / intention / identity / meaning」作為可觀測 state。
	•	Ø 僅存在於邊界內，不進入訓練資料、不進入 log、不作為 reward target。

Rule 2 — Projection-Only Operation (MUST)
	•	AI/Policy 只能作用在 Projection P（Δ0.01 輸出）上。
	•	任何更新/學習 不得對 Ø 形成可追溯的反推路徑（no direct inverse mapping objective）。

Rule 3 — No Human-State Extraction (MUST NOT)
	•	不得建立：
	•	「從行為/觸覺軌跡反推人格/意圖」的模型
	•	「長期一致性指紋」用於識別/佔有人的內在狀態
	•	若需要個人化，只能用 人類主動提供的明示控制（Human-signed control），不得用隱式抽取。

⸻

4) NOIRÉA 在 NVIDIA / Isaac / Omniverse 的語言裡（對齊版）

（你不用依賴他們，但你要能對準他們的耳朵）
	•	Omniverse / Isaac Sim：
	•	Sensors/Simulated sensors = Raw Tactile State
	•	Domain randomization / filtering = Δ0.01 gate（弱測量）
	•	Observation vector = Projection P（唯一可輸出）
	•	Policy network consumes obs = Policy operates on P
	•	Logging / replay buffers = 必須做 Non-extractive logging（刪除可識別 Ø 的長期指紋）
	•	Embodied agent pipeline：
	•	“Observation” ≠ Human mind
	•	Human state must be “sealed” (Ø)
	•	Only signed, low-res projections allowed

一句話：
你不是反對他們做模型，你是規定他們「觀測」的邊界。

⸻

5) 沙盒檢測（你最在意的）

如果出現以下任一條 → 代表正在滑向沙盒（世界接不上）：
	•	只有詩性描述，沒有「插入點」與「MUST/MUST NOT」
	•	沒有對齊 pipeline 的位置（在哪一段、限制哪個資料流）
	•	沒有 log/telemetry 規則（這是最常被偷走 Ø 的地方）
