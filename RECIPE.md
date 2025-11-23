# Craft 系统配置文档

## 配方的主要参数

| 参数 | 类型 | 描述 |
|----------|-----|----------|
| `craftRecipeID` | integer | 合成配方的唯一标识符 |
| `categoryID` | string | 配方所属分类（例如："Craft"） |
| `craftTitle` | string | 界面中显示的配方名称 |
| `craftDescription` | string | 配方描述 |
| `resultPreview` | string | 结果的预览图（物品 classname）。  
如果填写 classname，则预览显示物品模型；  
如果填写图标路径，则显示图标。  
<br><img width="142" height="59" src="https://github.com/user-attachments/assets/e09c9d1d-fe8b-466a-bf12-4c40552c1c83" />  
<img width="143" height="59" src="https://github.com/user-attachments/assets/4996c44a-0f5c-431f-92cb-8013166275c6" /> |
| `buttonCraftTitle` | string | 合成按钮上的文本。默认是“Создать предмет（创建物品）”，你可以自定义。  
<br><img width="191" height="112" src="https://github.com/user-attachments/assets/9ea6be84-4524-47a1-8eba-3a571f36ccdc" />  
<img width="213" height="127" src="https://github.com/user-attachments/assets/cc6383f5-3dd7-4f5e-beb8-7a7f6da8bbeb" /> |
| `progressTitle` | string | 合成进行中的进度文本。  
<br><img width="315" height="131" src="https://github.com/user-attachments/assets/941286af-41ae-4fe8-a378-431de0257912" />  
<img width="284" height="81" src="https://github.com/user-attachments/assets/0c71f9bd-8a2e-4575-98fc-98145c37124b" /> |
| `rarityColor` | string | 稀有度颜色，hex 格式（如 `"0xFF43A047"`） |
| `craftMode` | integer | 合成模式：0 – 队列模式；1 – 直接模式（无队列） |
| `craftTimeSec` | integer | 合成耗时（秒） |

## 结果生成参数

| 参数 | 类型 | 描述 |
|----------|-----|----------|
| `spawnOutsideWorkbench` | bool | 是否在工作台外生成结果（0=否，1=是） |
| `resultSpawnPosOffset` | array[float] | 结果生成位置偏移 [x, y, z] |
| `resultSpawnPosition` | array[float] | 结果生成的绝对位置 [x, y, z] |
| `resultSpawnOrientation` | array[float] | 结果的生成角度 [pitch, yaw, roll] |

## 反向合成（Decraft）参数

| 参数 | 类型 | 描述 |
|----------|-----|----------|
| `allowDecraft` | bool | 是否允许拆解（0=否，1=是） |
| `decraftNeedAttachments` | bool | 拆解是否需要附件（0=否，1=是） |
| `decraftNeedLearn` | bool | 拆解是否需要已学习该配方（0=否，1=是） |
| `decraftNeedPerk` | bool | 拆解是否需要特定技能（0=否，1=是） |

| 参数 | 类型 | 描述 |
|----------|-----|----------|
| `needToLearn` | bool | 使用配方前是否必须学习（0=否，1=是） |
| `deleteAfterLearn` | bool | 学习后是否删除配方（0=否，1=是） |
| `hideRecipeWithoutPerk` | bool | 未满足技能要求时是否隐藏配方（0=否，1=是） |
| `requireAllPerksInList` | bool | 是否需要列表内所有技能（0=否，1=是） |
| `needPerkToCraft` | array[integer] | 合成所需技能 ID 列表 |
| `needToChooseResult` | bool | 是否需要从多个结果中选择（0=否，1=是） |
| `showCraftWindowForResult` | bool | 合成后是否弹出结果窗口（仅单结果且非队列模式） |

## 经验和技能参数

| 参数 | 类型 | 描述 |
|----------|-----|----------|
| `addPerkPointsSkillTypes` | array[string] | 哪些技能类型会获得经验（如“HUNTING”） |
| `addPerkPointsValue` | array[float] | 对应技能增加的经验值 |

## 合成结果 (results)

| 参数 | 类型 | 描述 |
|----------|-----|----------|
| `classname` | string | 结果物品类 |
| `resultTitle` | string | 结果显示名称（空则使用默认） |
| `resultPreview` | string | 预览图（空则使用 classname） |
| `showResultAttachmentsInfo` | integer | 是否显示附件信息（0=否，1=是） |
| `chance` | float | 获得该结果的概率。  
如果所有结果 chance=0 → 全部生成；  
如果至少一个结果 chance>0 → 根据权重随机生成 1 个结果。 |

### 结果状态参数

| 参数 | 类型 | 描述 |
|----------|-----|----------|
| `health` | array[float] | 物品耐久 [固定值, 最小, 最大]；若固定值=-1，则在最小~最大之间随机 |
| `count` | array[integer] | 物品数量 |
| `quantity` | array[float] | 内容物数量 |
| `energy` | array[float] | 能量值 |
| `liquid` | integer | 液体类型（-1 或 0=无液体） |
| `foodStage` | integer | 食物阶段（-1=忽略） |
| `cleanness` | integer | 清洁度（-1=忽略） |

## 必需附件 (needAttachment)

| 参数 | 类型 | 描述 |
|----------|-----|----------|
| `isKindOf` | integer | 是否使用 isKindOf 检查（0=精确匹配，1=继承匹配） |
| `attachType` | string | 附件类名 |
| `attachSlot` | string | 工作台上的附件槽位 |
| `needElectricityOn` | bool | 是否需要供电（0=否，1=是） |
| `hideRecipeIfMissing` | bool | 缺少附件时是否隐藏配方（0=否，1=是） |
| `damageAfterCraft` | float | 合成后附件损坏量（必须为负值） |
| `decreaseQuantityAfterCraft` | float | 合成后减少附件内容量（正数） |

### 附件属性削减

| 参数 | 类型 | 描述 |
|----------|-----|----------|
| `decreaseAttachHealth` | object | { "类名": 减少值 } |
| `decreaseAttachQuantity` | object | { "类名": 减少值 } |

## 必需材料 (needIngredients)

| 参数 | 类型 | 描述 |
|----------|-----|----------|
| `isKindOf` | integer | 是否使用 isKindOf（0=精确，1=继承） |
| `itemTitle` | string | 材料名称（空则使用默认） |
| `itemClassname` | array[string] | 材料可用类名列表 |
| `itemPreview` | string | 材料预览（类名或图标路径） |
| `itemCount` | integer | 需要的数量 |
| `itemHealth` | integer | 最低耐久（不是百分比，是耐久等级） |
| `destroyItem` | integer | 合成后是否销毁材料（0=否，1=是） |

### 材料状态参数

| 参数 | 类型 | 描述 |
|----------|-----|----------|
| `quantityAsCount` | bool | 若启用，叠堆数量视为材料数量（例如布条会累计数量） |
| `itemQuantity` | array[float] | 内容物数量范围 |
| `itemEnergy` | array[float] | 能量值 |
| `itemFoodStage` | array[integer] | 可接受的食物阶段 |
| `itemCleanness` | integer | 清洁度要求 |
| `itemLiquidType` | integer | 液体类型 |
| `itemHaveEnergy` | integer | 是否必须有能量（0=否，1=是） |

### 材料在合成后的变化

| 参数 | 类型 | 描述 |
|----------|-----|----------|
| `itemDamageAfterCraft` | array[float] | 材料耐久减少 |
| `itemQuantityAfterCraft` | array[float] | 材料内容减少 |
| `itemDecraftCount` | float | 反向合成获得的数量 |
| `itemDecraftHealth` | float | 反向合成获得的耐久 |
| `itemQuantityEnergyDecreaseCoef` | float | 数量/能量减少系数 |
| `itemDecraftFoodStage` | integer | 反向合成的食物阶段 |

## 说明

🛠 物品耐久状态 (itemHealth)

| 数值 | 常量 | 含义 |
|------|--------------------|-------------------------|
| 0 | STATE_PRISTINE | 完好 |
| 1 | STATE_WORN | 轻微损耗 |
| 2 | STATE_DAMAGED | 中度损坏 |
| 3 | STATE_BADLY_DAMAGED | 重度损坏 |
| 4 | STATE_RUINED | 损毁不可用 |

🥩 食物阶段 (FoodStage)

| 数值 | 名称 | 描述 |
|------|---------|---------|
| 1 | RAW | 生的 |
| 2 | BAKED | 烤的 |
| 3 | BOILED | 煮的 |
| 4 | DRIED | 风干 |
| 5 | BURNED | 烧焦 |
| 6 | ROTTEN | 腐烂 |

📌 其他说明：
- 三元素数组格式为 `[固定值, 最小, 最大]`  
- 固定值=-1 或 0 → 使用随机范围  
- -1 通常表示“忽略此参数”  
- 颜色使用 0xFF 前缀（ARGB 格式）  
- bool 值为 `0=false`，`1=true`
