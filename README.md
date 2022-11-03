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
| ESDB-API-003 | 貼付位置一覧取得 |
| ESDB-API-004 | 対象一覧取得 |
| ESDB-API-005 | エンチャント検索（通常条件設定） |
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
| Key |	Type | Description |
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
| effect | string | 効果ト名 |
