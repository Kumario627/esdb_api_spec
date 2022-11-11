# 概要
ESDB の公開API一覧を記載する。

# API Endpoint  
```
https://wd5zeazzd9.execute-api.ap-northeast-1.amazonaws.com/Prod
```

# API一覧
API一覧を記載する。
詳細は各APIの詳細節を参照。
| API ID | Overview |
| ----- | ---- |
| [ESDB-API-001](#ESDB-API-001_エンチャント一覧取得) | エンチャント一覧取得 |
| [ESDB-API-002](#ESDB-API-002_効果一覧取得) | 効果一覧取得 |
| [ESDB-API-003](#ESDB-API-003_貼付位置一覧取得) | 貼付位置一覧取得 |
| [ESDB-API-004](#ESDB-API-004_対象一覧取得) | 対象一覧取得 |
| [ESDB-API-005](#ESDB-API-005_エンチャント検索通常条件設定) | エンチャント検索（通常条件設定） |
| [ESDB-API-006](#ESDB-API-006_エンチャント検索フリーワード) | エンチャント検索（フリーワード） |
| [ESDB-API-007](#ESDB-API-007_エンチャント情報取得id) | エンチャント情報取得（id) |
| [ESDB-API-008](#ESDB-API-008_ランクのエンチャント成功確率取得) | ランクのエンチャント成功確率取得 |
| [ESDB-API-009](#ESDB-API-009_下地一覧取得) | 下地一覧取得 |

## ESDB-API-001_エンチャント一覧取得
エンチャント一覧を全件取得する。  
### Path
```
/enchant/id
```
### Method
```
GET
```
### Input
`None`
### Output
Format:`JSON(Array)`
| Key | Type | Description |
| --- | ---- | ----------- |
| enchant_id | string | エンチャントID |
| enchant_name | string | エンチャント名 |
| enchant_name_2 | string | エンチャント別名 |
| enchant_name_en | string | エンチャント英名 |

## ESDB-API-002_効果一覧取得
効果一覧を全件取得する。
### Path
```
/effect/id
```
### Method
```
GET
```
### Input
`None`
### Output
Format:`JSON(Array)`
| Key |	Type | Description |
| --- | ---- | ----------- |
| effect_id | string | 効果ID |
| effect | string | 効果名 |

## ESDB-API-003_貼付位置一覧取得
貼付情報一覧を全件取得する。
### Path
```
/position/id
```
### Method
```
GET
```
### Input
`None`

### Output
Format:`JSON(Array)`
| Key | Type | Description |
| --- | ---- | ----------- |
| position_id | string | 位置ID |
| name | string | 位置名　|
| name_en | string | 位置名（英） |

## ESDB-API-004_対象一覧取得
対象一覧を全件取得する。
### Path
```
/target/id
```
### Method
```
GET
```
### Input
` None `

### Output
Format:`JSON(Array)`
| Key | Type | Description |
| --- | ---- | ----------- |
| target_code | string | 対象ID |
| target_name | string | 対象表示名 |

## ESDB-API-005_エンチャント検索(通常条件設定)
エンチャント通常検索処理の結果を返す。  
Inputを指定しない場合は全件取得する。

### Path
```
/detail
```
### Method
```
GET
```
### Input
Format: `Query string`  
参考)  
効果ID: [ESDB-API-002](#ESDB-API-002_効果一覧取得)  
位置ID: [ESDB-API-003](#ESDB-API-003_貼付位置一覧取得)  
対象ID: [ESDB-API-004](#ESDB-API-004_対象一覧取得)
| name | Description |
| ---- | ----------- |
| enchantName　| エンチャント名 |
| effect　| 効果ID |
| effectVal　| 効果の値 |
| range　| 以上: 1, 以下: 2　（効果の値が〜以上/以下を指定する。任意） |
| position　| 位置ID |
| rank　| ランク |
| rankRange　| 一致: 1, 以上: 2, 以下:3 |
| target　| 対象ID |


### Output
Format:`JSON`
| Key | Type | Description |
| --- | ---- | ----------- |
| enchant_list | array(object) | エンチャント情報の配列　詳細は*1参照 |
| effect_name | object | 効果名情報 詳細は*2参照 |

#### *1 enchant_list
enchant_list配列内オブジェクトの構成を示す。
| Key | Type | Description |
| --- | ---- | ----------- |
| enchant_id | string | エンチャントID |
| position_id | string | 位置ID |
| rank | string | ランク |
| rank_seq | number | ランクの内部シーケンス |
| rank_ignore_flg | string | ランクに関係なくエンチャント可能か 0:不可, 1:可 (ランクA以下は全て0) |
| enchant_name | string | エンチャント名 |
| enchant_name_2 | string | エンチャント別名 |
| enchant_name_en | string | エンチャント英名 |
| target_code | string | 対象コード |
| target_name | string | 対象表示名 |
| imp_flg | string | 実装済か 0:未実装 1:実装 |
| effect_kbn | string | 効果区分 |
| effect_name | string | エンチャントの効果区分 |
| route_name | string | 入手先 |
| disp_val | number | 効果の値 ※Input で effect の指定があった場合のみ返却される |
| invalid_target_flg | string | 貼付可否 0:可能, 1:不可能 *Input で target の指定があった場合のみ返却される |

effect_kbnは4種類存在する。  
画面表示時に色の出し分けをするための区分。
| Key | Description |
| --- | ----------- |
| increase | 増加 |
| decrease | 減少 |
| designated | 専用 |
| not-relevant | ランクに関係なくエンチャント可能 |

#### *2 effect_name
effect_name オブジェクトの構成を示す。  
※Input でeffect の指定があった場合のみ返却される
| Key | Type | Description |
| --- | ---- | ----------- |
| effect_id | string | 効果ID |
| effect | string | 効果表示名 |

## ESDB-API-006_エンチャント検索（フリーワード）
ヘッダ部検索バーの検索結果を返す。
Inputを指定しない場合は全件取得する。

### Path
```
/search
```
### Method
```
GET
```
### Input
Format: `Query string`
| name | Description |
| ---- | ----------- |
| search | 検索語句 |

### Output
Format:`JSON`
| Key | Type | Description |
| --- | ---- | ----------- |
| enchant_list | array(object) | エンチャント情報の配列　詳細は*1参照 |

#### *1 enchant_list
enchant_list配列内オブジェクトの構成を示す。
| Key | Type | Description |
| --- | ---- | ----------- |
| enchant_id | string | エンチャントID |
| position_id | string | 位置ID |
| rank | string | ランク |
| rank_seq | number | ランクの内部シーケンス |
| rank_ignore_flg | string | ランクに関係なくエンチャント可能か 0:不可, 1:可 (ランクA以下は全て0) |
| enchant_name | string | エンチャント名 |
| enchant_name_2 | string | エンチャント別名 |
| enchant_name_en | string | エンチャント英名 |
| target_name | string | 対象表示名 |
| imp_flg | string | 実装済か 0:未実装 1:実装 |
| invalid_target_flg | string | 0固定 |
| effect_kbn | string | 効果区分 |
| effect_name | string | エンチャントの効果区分 |
| route_name | string | 入手先 |

## ESDB-API-007_エンチャント情報取得（id)
エンチャントIDに紐づくエンチャント情報を取得する. 
  
参考)  
エンチャントID: [ESDB-API-001](##ESDB-API-001_エンチャント一覧取得) 

### Path
```
/detail/:enchantId
```
### Method
```
GET
```
### Input
Format: `Path Parameter`
| name | Description |
| ---- | ----------- |
| enchantId | エンチャントIDを指定する(ex. 00000001) |

### Output
Format:`JSON`
| Key | Type | Description |
| --- | ---- | ----------- |
| enchant_id | string | エンチャントID |
| position_id | string | 位置ID |
| rank | string | ランク |
| rank_ignore_flg | string | 0固定 |
| enchant_name | string | エンチャント名 |
| enchant_name_2 | string | エンチャント別名 |
| enchant_name_en | string | エンチャント英名 |
| target_code | string | 対象コード |
| target_name | string | 対象表示名 |
| imp_flg | string | 実装済か 0:未実装 1:実装 |
| effect_kbn | string | 効果区分 |
| effect_name | string | エンチャントの効果区分 |
| route_name | string | 入手先 |

## ESDB-API-008_ランクのエンチャント成功確率取得

### Path
```
/rank/:rank
```
### Method
```
GET
```
### Input
Format: `Path Parameter`
| name | Description |
| ---- | ----------- |
| rank | ランクを指定（ex.F) |

### Output
Format:`JSON`
| Key | Type | Description |
| --- | ---- | ----------- |
| rank | string | ランク |
| normal_rate | string | 通常成功率 |
| elite_rate | string | エリート成功率 |
| elf_rate | string | エルフ成功率 |
| ancient_rate | string | 古代成功率 |
| rare_holy_rate | string | 稀代成功率  |
| normal_rate_thu | string | 通常木曜成功率  |
| elite_rate_thu | string | エリート木曜成功率 |
| elf_rate_thu | string | エルフ木曜成功率 |
| ancient_rate_thu | string | 古代木曜成功率 |
| rare_holy_rate_thu | string | 稀代木曜成功率 |

## ESDB-API-009_下地一覧取得

### Path
```
/ground/:enchantId
```
### Method
```
GET
```
### Input
Format: `Path Parameter`
| name | Description |
| ---- | ----------- |
| enchantId | エンチャントIDを指定する(ex. 00000134)  |

### Output
Format:`JSON`
| Key | Type | Description |
| --- | ---- | ----------- |
| ground | array | target_enchantに対して使用可能なエンチャントをランク毎に格納 詳細は※1参照 |
| target_enchant | object | 検索条件に指定したエンチャントIDに紐づくエンチャント情報 詳細は※2参照 |

#### *1 ground
各ランクに紐づく下地の一覧。  

| Key | Type | Description |
| --- | ---- | ----------- |
| rank | string | 下地の該当ランク |
| enchant_list | array | エンチャント情報一覧 |

enchant_listは下記のように定義されている。
| Key | Type | Description |
| --- | ---- | ----------- |
| enchant_id | string | エンチャントID |
| position_id | string | 位置ID |
| rank | string | ランク |
| enchant_name | string | エンチャント名 |
| enchant_name_2 | string | エンチャント別名 |
| enchant_name_en | string | エンチャント英名 |

#### *2 target_enchant
下地を検索したエンチャント自身の情報
| Key | Type | Description |
| --- | ---- | ----------- |
| enchant_id | string | エンチャントID |
| enchant_name | string | エンチャント名 |
| enchant_name_2 | string |  エンチャント別名 |
| enchant_name_en | string | エンチャント英名 |
| position_id | string | 位置ID |
| rank | string | ランク |
| target_code | string | 対象コード |
