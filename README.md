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
| ESDB-API-006 | エンチャント検索（フリーワード） |
| ESDB-API-007 | エンチャント情報取得（id) |
| ESDB-API-008 | ランクのエンチャント成功確率取得 |
| ESDB-API-009 | 下地一覧取得 |

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
| name | Description |
| ---- | ----------- |
| enchantName　| エンチャント名 |
| effect　| 効果ID |
| effectVal　| 効果の値 |
| range　| 以上: 1, 以下: 2 |
| position　| 位置ID |
| rank　| ランク |
| rankRange　| 一致: 1, 以上: 2, 以下:3 |
| target　| 対象ID |


### Output
Format:`JSON(Array)`
| Key | Type | Description |
| --- | ---- | ----------- |
|   |  |   |
