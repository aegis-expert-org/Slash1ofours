<!-- 產品／專案：Slash1ofours｜法人／事業體：斜槓104 / Slash104（獨立法人；完整法定名稱 [暫定]／[待確認]）｜日期：2026-11-11（Asia/Taipei）｜草稿 v0.3 -->
# Slash1ofours
C2-AE-S14 斜槓104 Slash104 企業級領域知識與智財數位分身平台  for 中大型企業、研發團隊、顧問機構
# 斜槓104 (slash1ofours.com) - 企業級領域知識與智慧財產數位分身授權平台

[![Repository Archetype: Functional App](https://img.shields.io/badge/Archetype-C3--Functional--App-blue.svg)](#)
[![PMO ID](https://img.shields.io/badge/PMO--ID-C3--AE--S14--F-orange.svg)](#)
[![Domain](https://img.shields.io/badge/Domain-aegis.expert-green.svg)](#)
[![Security Level](https://img.shields.io/badge/Security-FHE%20%2F%20Zero--Knowledge%20Enterprise%20ACL-critical.svg)](#)

> **核心定位**：延伸自「斜槓一二三」，主體由**個人專家**升級為**公司、團隊與專案組**。分身代表整組團隊領域知識與智慧財產（IP），而非單一個人。平台本身**不訓練模型、不收存明文知識包**，而是將多位成員在地端 **密文智庫（EncryMind）** 受保護區貢獻、審核併入的組織智慧，轉化為「歸屬公司、多層授權（對內/對外）、可計量、可稽核」之企業數位分身權利交易與驗證中樞。

---

## 1. 核心架構哲學與原則

1. **分身與智財歸屬公司，非個人成員**：知識由授權成員餵入公司指定 NAS，經審核併入分身。分身資產與授權利益歸法人或團隊所有，人員離職或調組不帶走知識明文。
2. **審核閘門與智財標籤隔離**：未經審核的資料不得被正式分身引用；標註為「不得外授權」的機密資料，只能進內部授權分身，嚴禁出現在對外標售分身。
3. **買授權（能問、能解），不交出知識本體**：買方或內部使用者僅取得向企業分身提問並解密答案的權利（Inference-only Capability），原始文件、製程配方與模型權重永不出地端 NAS。
4. **雙層授權矩陣（對內治理 vs 對外標售）**：
   - **對內**：依角色（Owner / Admin / Contributor / Reviewer / Member）與團隊配置權限，離職即時撤銷。
   - **對外**：公司簽發 B2B 授權合約與 USB 綁定憑證，預設嚴禁再授權（No Re-authorization）。
5. **硬體在位驗證（Hardware-in-the-Loop）**：解密權利透過實體 USB 安全金鑰（FIDO2 / CTAP2 / Secure Element）執行；USB 不在位時，即使權限有效亦無法解出答案，拔除即清除記憶體明文。
6. **匿名使用但不可否認**：平台與外部節點無法反推誰在問、問了什麼；每次調用僅留下可驗證的零知識審計收據（Audit Receipt）。

---

## 2. 與「斜槓一二三」架構對應矩陣

| 構面 | 斜槓一二三 (`slash1to3.com`) | 斜槓104 (`slash1ofours.com`) |
| :--- | :--- | :--- |
| **法律與經濟主體** | 個人專家 | 公司、法人、團隊、專案組 |
| **分身代表內容** | 個人專業知識與經歷 | 團隊跨職能領域知識與企業智財（IP） |
| **知識餵入途徑** | 本人直接匯入地端 NAS | 具權限成員各自餵入，**需經審核者（Reviewer）核可** |
| **資產所有權** | 專家個人持有 | **公司實體完全持有**（成員離職不影響資產） |
| **授權架構** | 個人直接簽發予外部買方 | **雙層架構**：對內部成員分級授權 / 對外部客戶商業標售 |
| **標售展示** | 個人分身資產卡片（顯示已轉出 N 個分身） | 企業團隊能力卡片（不公開內部成員名單與原稿） |

---

## 3. 系統功能架構六大維度

```
                       ┌──────────────────────────────────────────────┐
                       │          斜槓104 企業平台控制平面             │
                       │ (公司帳號 / 組織架構 / 審核流程 / 授權與帳務)    │
                       └──────────────────────┬───────────────────────┘
                                              │ (授權驗證 / 狀態即時同步)
        ┌─────────────────────────────────────┴─────────────────────────────────────┐
        ▼                                                                           ▼
┌───────────────────────────────────────┐                 ┌───────────────────────────────────────┐
│         企業側密文智庫叢集            │                 │         提問終端 (內部成員 / 外部買方)  │
│ ┌───────────────────────────────────┐ │                 │ ┌───────────────────────────────────┐ │
│ │ 知識審核與受保護儲存區             │ │                 │ │ 實體 USB 安全金鑰 (FIDO2 / SE)    │ │
│ │ (自有 / 授權使用 / 不得外授權標記) │ │    密文推理通道  │ └─────────────────┬─────────────────┘ │
│ └─────────────────┬─────────────────┘ │  (FHE / TLS / DPoP)│ ┌─────────────────▼─────────────────┐ │
│ ┌─────────────────▼─────────────────┐ │ ◄─────────────► │ │ 提問端 Client (無暫存 / 記憶體清除) │ │
│ │ 本機 SLM / RAG 推理 (公司分身)    │ │                 │ └───────────────────────────────────┘ │
│ └───────────────────────────────────┘ │                 │                                       │
└───────────────────────────────────────┘                 └───────────────────────────────────────┘
```

### 3.1 公司與組織權限治理
* **多層組織架構**：支援建立公司帳號（與個人帳號分離，個人可兼屬多公司），下設處、部門、團隊與專案組。
* **五階角色存取控制 (RBAC)**：
  - `OWNER`（擁有者）：公司分身所有權、標售定價、分身移轉與下架。
  - `ADMIN`（管理員）：成員調配、NAS 節點綁定、簽發對內/對外授權金鑰。
  - `REVIEWER`（審核者）：審核成員提交之知識包，決定是否併入正式分身。
  - `CONTRIBUTOR`（貢獻者）：餵入負責範疇的資料至 NAS 受保護區。
  - `CONSUMER`（使用者）：持授權金鑰向分身進行受控提問推理。
* **人員異動即時連動**：成員離職、調組或撤權時，平台標記失效並秒級同步至 NAS 側，新請求立即阻斷。已併入之知識留存公司，人員無法匯出明文。

### 3.2 智財管理與知識審核管線
* **多標籤智財狀態機制**：
  - `IP_PROPRIETARY`：自有智慧財產，可納入對內與對外分身。
  - `IP_LICENSED`：第三方授權使用，需遵循授權條款。
  - `IP_INTERNAL_ONLY`：**嚴禁外授權**，僅能進入內部管理分身，對外標售分身邏輯隔離無法檢索。
* **審核者核可機制（Reviewer Gate）**：未經審核的知識片段僅留存暫存區，地端 RAG / 模型微調不予索引，對外回答完全隔離。
* **單一實體繁衍多專精分身**：依業務線建立「製程安全分身」、「研發配方分身」、「售後客服分身」，各自具備獨立 Skills 規範與邊界。

### 3.3 授權與金鑰體系
* **對內角色授權**：依職級與部門批量簽發短命權限憑證（Capability Token，有效期限 5–15 分鐘）。
* **對外商業授權**：由管理員簽發，約束調用次數（Quota）、有效期限（Valid Until）與領域範疇。預設 `REAUTHORIZE=FALSE`。
* **多金鑰並行支援**：單一企業分身可發行多組獨立金鑰，同時授權多家外部合作夥伴，彼此額度與審計紀錄獨立。
* **硬體在位控制**：提問端僅在 USB 插入並通過 FIDO2 二次驗證時解密答案；USB 拔除瞬間立即觸發 Client 記憶體 Wipe。

### 3.4 智慧轉型標售市場
* **企業分身卡片**：展示發行企業、團隊領域、Skills 清單、能答範圍、不能答邊界、是否支援 USB。保護企業隱私，不公開內部人員名冊與原始技術文件。
* **防洩漏試問機制**：未付款前僅提供合成示範或回傳混淆密文樣本，嚴禁透過 Prompt 逆向工程刺探商業機密。
* **標的物為權利合約**：交易完成後交付「授權物件（Grant Object）」與硬體金鑰啟用憑證，永不交付原始資料庫。

### 3.5 匿名使用與不可否認審計
* **全鏈路密文推理**：提問端直連企業 NAS，平台控制平面不中繼明文，不落地問答記錄。
* **零知識審計收據 (Audit Receipt)**：
  - 日誌僅記錄：`企業 ID`、`分身 ID`、`授權不可逆指紋 (Grant Hash)`、`時間戳記`、`額度消耗`、`節點簽名`。
  - 企業管理層僅可檢視用量與成功率，嚴禁調閱個別員工或買方的問答內容明文。
* **零明文爭議仲裁**：客訴爭議僅比對授權範圍、有效期限、額度扣減紀錄與不可否認收據，不調閱對話文本。

---

## 4. 核心資料模型規格

### 4.1 企業授權物件規格 (Enterprise Grant Schema)
```json
{
  "$schema": "https://slash1ofours.com/schemas/grant-v1.json",
  "grant_id": "egr_01JB89A...",
  "corp_id": "corp_taiwan_semitech_01",
  "twin_id": "twin_wafer_yield_expert",
  "scope_type": "EXTERNAL_COMMERCIAL",
  "holder_info": {
    "entity_name": "Partner Corp B",
    "holder_thumbprint": "sha256:d41d8cd98f00b204e9800998ecf8427e..."
  },
  "ip_boundary": {
    "allow_internal_only_ip": false,
    "allowed_skill_domains": ["etching_diagnostics", "defect_analysis"]
  },
  "usb_policy": {
    "hardware_required": true,
    "fido2_aaguid_allowlist": ["4a5c90..."]
  },
  "constraints": {
    "valid_from": "2026-11-01T00:00:00Z",
    "valid_until": "2027-04-30T23:59:59Z",
    "quota_queries_total": 2000,
    "max_concurrency": 4,
    "allow_reauthorization": false
  },
  "revocation_epoch": 2,
  "state": "ACTIVE"
}
```

### 4.2 知識包審核登錄規格 (Knowledge Ingestion Schema)
```json
{
  "$schema": "https://slash1ofours.com/schemas/ingestion-v1.json",
  "ingestion_id": "ing_993412...",
  "corp_id": "corp_taiwan_semitech_01",
  "contributor_id": "usr_engineer_42",
  "node_id": "nas_node_fab3_edge",
  "ip_classification": "IP_INTERNAL_ONLY",
  "review_status": "APPROVED",
  "reviewer_id": "usr_lead_architect_07",
  "indexed_twin_targets": ["twin_internal_rnd_helper"],
  "content_manifest_hash": "sha256:88d4266fd4e6338d13b845fcf289579d...",
  "approved_at": "2026-10-15T09:12:00Z"
}
```

---

## 5. Repository 檔案結構骨架

```
aegis-slash1ofours-app/
├── README.md                     # 本專案核心總覽與架構規範說明
├── ARCHITECTURE.md               # 企業多租戶、邊界隔離與密文握手時序
├── REQUIREMENTS.md               # 企業追溯需求矩陣 (FR-xxx, NFR-xxx, SEC-xxx)
├── QA-ACCEPTANCE.md              # 七道 QA 閘門驗收檢核標準與測試案例
├── TEST-PLAN.md                  # 單元、組織越權、併發扣額與模糊測試計畫
├── DEPLOYMENT.md                 # 混合雲佈署手冊 (SaaS Gateway + 企業地端 NAS 集群)
├── SECURITY.md                   # 智財保護、個資法遵 (PDPA/GDPR) 與密鑰控管指南
├── CONTRIBUTING.md               # PR 流程、分支策略與 CODEOWNERS 說明
│
├── .github/
│   ├── CODEOWNERS                # 模組審查權責分配 (依 security, crypto, auth 劃分)
│   ├── pull_request_template.md  # PR 提交檢核模板
│   └── workflows/
│       ├── ci-gate-checks.yml    # Build, Lint, TypeCheck, Unit Tests
│       └── security-scan.yml     # Secret Scanning, SAST, SBOM, Dependency Check
│
├── apps/
│   ├── enterprise-portal/        # 企業控制台 (團隊/審核/分身管理/市場上架 Next.js)
│   ├── rights-gateway/           # 雙層授權檢驗、額度原子鎖扣減與收據簽發服務
│   └── corp-nas-agent/           # 運行於企業地端密文智庫的守護程序 (Daemon)
│
├── packages/
│   ├── crypto-core/              # FIDO2 硬體驗證、短命 JWT、不可逆審計指紋庫
│   ├── ip-governance/            # 智財標籤隔離、審核狀態機與 Skills 邊界檢查器
│   ├── protocol-schemas/         # JSON Schema, protobuf 與 OpenAPI 企業規格
│   └── audit-logger/             # 匿名不可否認企業審計收據產生器
│
└── tests/
    ├── e2e/                      # 完整流程：多成員貢獻→審核→雙層授權→持鑰提問
    ├── mock-corp-nas/            # 用於 CI/CD 自動化測試之模擬企業 NAS 叢集
    └── security-pentest/         # 離職員工存取穿透、智財標籤越權與重放攻擊驗證
```

---

## 6. 本地開發與快速上手

### 6.1 前置環境需求
- Node.js `>= 20.x`
- Docker & Docker Compose (啟動本機 Redis 額度原子鎖、PostgreSQL 與模擬 NAS 節點)
- pnpm `>= 9.x`
- 相容 FIDO2 / CTAP2 之實體安全金鑰（或本機虛擬 WebAuthn Authenticator）

### 6.2 啟動本機開發環境
```bash
# 1. 複製代碼庫
git clone https://github.com/aegis-expert/aegis-slash1ofours-app.git
cd aegis-slash1ofours-app

# 2. 安裝相依模組
pnpm install

# 3. 啟動相依基礎設施與模擬企業 NAS 叢集
docker compose -f docker/docker-compose.dev.yml up -d

# 4. 初始化環境變數
cp .env.example .env.local

# 5. 啟動企業控制台與 Rights Gateway
pnpm dev
```

### 6.3 執行整合測試與企業資安防護檢驗
```bash
# 執行所有單元測試與智財狀態機檢驗
pnpm test

# 模擬完整多成員知識審核併入與對內/對外授權提問流程
pnpm test:e2e:enterprise-flow

# 執行離職員工撤權即時阻斷驗證 (Revocation Sync Test)
pnpm test:security:revocation-barrier

# 驗證「不得外授權」資料是否徹底被對外分身隔離
pnpm test:security:ip-isolation
```

---

## 7. QA 品質閘門檢驗標準 (7-Gate Governance)

依循專案 PMO 規範，所有 PR 與發布均需通過七道品質驗收閘門：

| 閘門代號 | 閘門名稱 | 核心查核重點 |
| :--- | :--- | :--- |
| **G1** | **Scope Ready** | 需求符合 MVP 邊界；確認無跨公司共編、無個人/公司混用、無原始檔案下載。 |
| **G2** | **Design Ready** | 雙層授權架構設計完備；標記為 `IP_INTERNAL_ONLY` 之資料流具備邏輯隔離證明。 |
| **G3** | **Build Ready** | CI 構建通過，單元測試覆蓋率 $\ge 85\%$，靜態安全掃描零高危弱點。 |
| **G4** | **Integration Ready** | 平台 Gateway 與企業 NAS Agent 密文握手成功，人員停權狀態同步延遲 $< 3$ 秒。 |
| **G5** | **Content & Legal** | 標售頁 Skills 邊界清晰；符合台灣個人資料保護法（PDPA）與營業秘密法免責合規。 |
| **G6** | **Release Ready** | USB 拔除記憶體即時清除、額度並發扣減競爭條件（Race Condition）壓力測試通過。 |
| **G7** | **Post-Release** | 企業不可否認收據稽核鏈路通暢，監控系統確認無任何問答明文洩漏至平台日誌。 |

---

## 8. PMO 角色職責與聯絡矩陣

依照專案組織控管規範，本模組權責人員與自動轉發聯絡信箱配置如下：

* **Repo Admin / 權限維護**：`admin-aegis-slash1ofours-app@aegis.expert`
* **Lead Architect / 開發負責人**：`dev-aegis-slash1ofours-app@aegis.expert`
* **QA & 驗收簽核團隊**：`qa-aegis-slash1ofours-app@aegis.expert`
* **Collaborator 協同開發組**：`collab-aegis-slash1ofours-app@aegis.expert`
* **全域資安應變應急 (CSIRT)**：`github-security@wonderland.center`


## v0.3 變更註記（2026-11-11，Asia/Taipei）

品牌：斜槓104 / Slash104；官方網域 `slash1ofours.com`，備用 `1ofour.com`。兩者不代表網域持有人或法人登記已核驗。

僅修正本次涉及之品牌顯示名稱、網域文字及與 t12u 直接衝突的法人關係段落；repo／org、技術代碼、URL、路徑、分支及 email local part 均未變更。品牌與網域確認不代表內容核准；本文件為草稿 v0.3，其他來源規格僅供參考，未驗證的功能、效能、時程及合規不得視為核准。

### 人工審核清單

- 完整法定名稱、登記資訊、設立沿革、網域持有人與技術協作／託管契約仍以已確認錨點為限，其他 [待確認] 標註維持。
- 既有版權權利人與授權條款未由本次品牌修訂推定變更；請確認 README 的版權行及 LICENSE 第 189 行 `Copyright [yyyy] [name of copyright owner]` 範本尚未填寫之權利人與年份。
- 保留的技術 URL／徽章／代碼若含歷史文字，並非現行品牌或法人歸屬聲明；如需替換 URL 或改名須另行確認。
- 其餘效能、法遵、交付與產品主張未經核驗，均待人工審核，不因本次修字或 PR 合併視為核准。
