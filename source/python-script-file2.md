---
title: python script file2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'file2'


## python file2

Python example: file2

```python
# ファイル読込
filename = "data.csv"
df = pd.read_csv(filename,encoding="SHIFT-JIS",skiprows=4)

# 列名の変更
df_rain.columns = ["datetime", "rain", "現象なし情報","品質情報","均質番号"]

# 日時をタイムスタンプに変換
df_rain["datetime"] = df_rain.datetime.map(lambda _: pd.to_datetime(_))

# 日時をインデックスに設定
df_rain.index = df_rain.pop("datetime")

# グラフ表示
df_level.level.plot(figsize=(15,5))
df_rain.rain.plot(figsize=(15,5))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
