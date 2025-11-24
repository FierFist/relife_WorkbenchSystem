# Craft 配方示例说明

下面的示例展示了一个完整的合成配方结构，包括基本信息、结果产物、所需材料等内容。  
你可以根据需要复制此示例并修改相应字段。

---

## 配方基本参数

| 字段 | 类型 | 说明 |
|------|------|------|
| `craftRecipeID` | integer | 配方唯一 ID，用于区分不同配方 |
| `categoryID` | string | 配方所属分类，留空时显示在默认分类中 |
| `craftTitle` | string | 配方名称（界面显示） |
| `craftDescription` | string | 配方介绍（可留空） |
| `resultPreview` | string | 合成结果预览，可为物品类名或图标路径 |
| `buttonCraftTitle` | string | “开始合成”按钮文本（默认空为系统文本） |
| `progressTitle` | string | 合成过程中的进度文本（默认空为系统文本） |
| `rarityColor` | string | 稀有度颜色（HEX 格式，如 `0x75fa576a`） |
| `craftMode` | integer | 0 = 队列模式；1 = 直接模式 |
| `craftTimeSec` | integer | 合成所需时间（秒） |

---

## 结果生成设置

| 字段 | 类型 | 说明 |
|------|-------|------|
| `spawnOutsideWorkbench` | integer | 是否在工作台外生成物品（1 = 是，0 = 否） |
| `resultSpawnPosOffset` | float[3] | 相对偏移坐标 `[x, y, z]` |
| `resultSpawnPosition` | float[3] | 绝对生成坐标 `[x, y, z]` |
| `resultSpawnOrientation` | float[3] | 生成物品的旋转角度 `[pitch, yaw, roll]` |

---

## 可否反向合成（Decraft）

| 字段 | 类型 | 说明 |
|------|------|------|
| `allowDecraft` | integer | 是否允许拆解该物品 |
| `decraftNeedAttachments` | integer | 拆解时是否需要附件 |
| `decraftNeedLearn` | integer | 拆解是否必须学习过该配方 |
| `decraftNeedPerk` | integer | 拆解是否需要技能 |

---

## 学习与技能相关

| 字段 | 类型 | 说明 |
|------|------|------|
| `needToLearn` | integer | 是否必须学习之后才可使用配方 |
| `deleteAfterLearn` | integer | 学习后是否删除配方物品 |
| `hideRecipeWithoutPerk` | integer | 未满足技能要求是否隐藏配方 |
| `requireAllPerksInList` | integer | 是否需要列表中所有技能 |
| `needPerkToCraft` | array[int] | 合成所需技能 ID |
| `needToChooseResult` | integer | 是否多结果可选 |
| `showCraftWindowForResult` | integer | 合成后是否显示结果弹窗 |

---

## 结果结构（results）

| 字段 | 类型 | 说明 |
|------|------|------|
| `classname` | string | 结果物品类名 |
| `resultTitle` | string | 显示名称（为空则用默认） |
| `resultPreview` | string | 预览图（为空则使用 classname） |
| `showResultAttachmentsInfo` | integer | 是否显示附件信息 |
| `chance` | float | 权重概率（0 = 全部生成；>0 = 按权重随机） |

---

### 结果状态（health/count/quantity 等）

- `"health": [1.0, -1, -1]` → 固定耐久 1.0  
- `"count": [1, -1, -1]` → 固定数量 1  
- `"quantity": [-1, -1, -1]` → 忽略数量  
- `"attachmentList"` → 结果附带的附件（例如弹匣）

---


## 合成后材料变化说明

```text
"itemQuantityAfterCraft": [-10.0, 0.0, 0.0]
该材料在合成后会 减少 10 单位内容物。

---

## 所需材料（needIngredients）

| 字段 | 类型 | 说明 |
|------|------|------|
| `isKindOf` | integer | 是否使用 isKindOf 检查 |
| `itemClassname` | array[string] | 可用材料类名列表 |
| `itemPreview` | string | 预览图（类名或图标） |
| `itemCount` | integer | 所需材料数量 |
| `quantityAsCount` | integer | 是否按叠堆数量计算 |
| `itemQuantity` | float[] | 内容物要求（如 10 = 固定 10） |
| `itemHealth` | integer | 最低耐久等级（0–4） |
| `destroyItem` | integer | 合成后是否销毁材料 |

---

[
    {
        "craftRecipeID": 1,
        "categoryID": "",
        "craftTitle": "AKM",
        "craftDescription": "",
        "resultPreview": "AKM",
        "buttonCraftTitle": "",
        "progressTitle": "",
        "rarityColor": "0x75fa576a",
        "craftMode": 0,
        "craftTimeSec": 20,
        "spawnOutsideWorkbench": 1,
        "resultSpawnPosOffset": [0, 0, 0],
        "resultSpawnPosition": [0, 0, 0],
        "resultSpawnOrientation": [0, 0, 0],
        "allowDecraft": 0,
        "decraftNeedAttachments": 0,
        "decraftNeedLearn": 0,
        "decraftNeedPerk": 0,
        "needToLearn": 0,
        "deleteAfterLearn": 0,
        "hideRecipeWithoutPerk": 0,
        "requireAllPerksInList": 0,
        "addPerkPointsSkillTypes": [],
        "addPerkPointsValue": [],
        "needPerkToCraft": [],
        "needToChooseResult": 1,
        "showCraftWindowForResult": 1,

        "results": [
            {
                "classname": "AKM",
                "resultTitle": "",
                "resultPreview": "",
                "showResultAttachmentsInfo": 1,
                "chance": 0,
                "health": [1, -1, -1],
                "count": [1, -1, -1],
                "quantity": [-1, -1, -1],
                "energy": [-1, -1, -1],
                "liquid": -1,
                "foodStage": -1,
                "cleanness": -1,

                "attachmentList": [
                    {
                        "classname": "Mag_AKM_Drum75Rnd",
                        "resultTitle": "",
                        "resultPreview": "",
                        "showResultAttachmentsInfo": 1,
                        "chance": 0,
                        "health": [1, -1, -1],
                        "count": [1, -1, -1],
                        "quantity": [5, -1, -1],
                        "energy": [-1, -1, -1],
                        "liquid": -1,
                        "foodStage": -1,
                        "cleanness": -1,
                        "attachmentList": []
                    }
                ]
            }
        ],

        "needAttachment": [],

        "needIngredients": [
            {
                "isKindOf": 1,
                "itemTitle": "",
                "itemClassname": ["Apple"],
                "itemPreview": "Apple",
                "itemCount": 1,
                "quantityAsCount": 1,
                "itemQuantity": [10, -1],
                "itemHealth": 3,
                "itemEnergy": [-1, -1],
                "itemFoodStage": [],
                "itemCleanness": -1,
                "itemLiquidType": -1,
                "itemHaveEnergy": 0,
                "destroyItem": 0,
                "itemDamageAfterCraft": [0, 0, 0],
                "itemQuantityAfterCraft": [-10, 0, 0],
                "itemDecraftCount": 0,
                "itemDecraftHealth": 0,
                "itemQuantityEnergyDecreaseCoef": 0,
                "itemDecraftFoodStage": 0
            }
        ]
    }
]
