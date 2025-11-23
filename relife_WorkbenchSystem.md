# 配置参数说明

## 基本参数

| 参数 | 类型 | 描述 |
|----------|-----|----------|
| `UIMainColor` | array[3] | UI 主颜色的 RGB 值 (0-255) （已无实际用途） |
| `addSkillPointsOfflinePlayer` | integer | 是否为离线玩家增加技能点（0 = 关闭） |
| `allowCraftInPlayer` | integer | 是否允许在玩家背包中进行合成（1 = 允许，0 = 禁止） |
| `debugResaveConfig` | integer | 重新保存配置的调试模式（0 = 关闭） |
| `adminSteamID` | array | 具有权限在线更新配置的管理员 SteamID 列表 |

## craftInPlayerSettings

玩家背包内合成的设置。

| 参数 | 类型 | 描述 |
|----------|-----|----------|
| `handleQueueMode` | integer | 合成队列处理模式（-1 = 默认；0 = 队列 + 直接；1 = 仅直接合成） |
| `coefCraftTime` | float | 合成时间系数（倍率） |
| `availableCategories` | array | 玩家可用的合成分类 |
| `attachmentList` | array | 可用的工具槽位列表 |
| `recipeList` | array | 可用的配方 ID 列表 |
| `maxQueue` | int | 最大队列数量 |

## attachmentsList

用于不同工具/设备的配置对象数组。

| 参数 | 类型 | 描述 |
|----------|-----|----------|
| `attachType` | string | 工具类型（如 "Gloves", "RLF_BenchGrinder"） |
| `isSlot` | bool | 是否按槽位名称而非物品名称查找 |
| `consumeElectricPerSec` | float | 每秒耗电量 |
| `coefCraftingTime` | float | 合成时间系数（0.5 = 两倍速度） |
| `allowRepairableWithKitsFind` | integer | 是否允许查找可修复物品（1 = 是，0 = 否） |
| `allowKindOfItems` | integer | 允许的物品类型（1 = 允许） |
| `repairableWithKitsAllow` | array | 允许修复的修理工具 ID 列表 |
| `itemAllowUseOnAttach` | array | 可在此工具上使用的物品 |
| `itemDisallowUseOnAttach` | array | 禁止在此工具上使用的物品 |
| `floatParamArray` | array[2] | 附加浮点参数数组（取决于工具类型） |

## categoryList

合成分类数组。

| 参数 | 类型 | 描述 |
|----------|-----|----------|
| `categoryID` | string | 分类唯一标识符 |
| `categoryTitle` | string | 分类标题（可使用本地化键） |
| `categoryIcon` | string | 分类图标路径 |

## workbenchList

工作台配置对象数组。

| 参数 | 类型 | 描述 |
|----------|-----|----------|
| `allowRemoveQueueOtherPlayer` | integer | 是否允许其他玩家删除队列（0 = 否，1 = 是） |
| `uiTitleText` | string | UI 标题文本 |
| `classnameWorkbench` | string | 游戏中的工作台类名 |
| `handleQueueMode` | integer | 队列处理模式（-1 = 默认配置；0 = 两种模式；1 = 仅直接模式） |
| `coefCraftTime` | float | 合成时间系数（1.1 = 慢 10%） |
| `canPlayerDeattachTools` | integer | 玩家是否可以取下工具（1 = 是，0 = 否） |
| `ignoreBlockDeattachItems` | array | 无视阻止拆卸的物品列表 |
| `canPlayerDecraft` | integer | 玩家是否可以分解物品（1 = 是，0 = 否） |
| `enableIsKindOfToolList` | integer | 启用类型检查（1 = 是，0 = 否） |
| `decraftToolsList` | array | 用于分解的工具列表 |
| `attachmentList` | array | 可用的工具槽位列表 |
| `availableCategories` | array | 可用的配方分类 |
| `maxQueue` | int | 最大队列数量 |
| `recipeList` | array | 可用配方 ID 列表 |

## craftRecipesList

| 参数 | 类型 | 描述 |
|----------|-----|----------|
| `craftRecipesList` | array | 合成配方数组，不可修改，系统会自动加载 |

## 说明

- 以 `#STR_` 开头的值表示使用本地化系统  
- 图标路径为相对路径，从模组根目录开始  
- 合成时间系数：  
  - 小于 1.0 → 加速  
  - 大于 1.0 → 减速
