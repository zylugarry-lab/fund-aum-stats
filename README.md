# 公募基金规模统计

用两份公募季报 Excel 生成九分类 / 非货规模统计与排名台账（规则修订版）。

## 网页版（上传即生成）

打开 GitHub Pages 页面，选择**当期**与**上期**季报，点击生成后下载 Excel。  
计算在浏览器本地完成（Pyodide），文件不会上传到服务器。

## WorkBuddy 技能

将 `skill/` 目录导入 WorkBuddy Skills，或使用桌面分发的 zip。

```bash
python3 skill/run_stats.py 当期季报.xlsx 上期季报.xlsx
```

## 本地预览网页

```bash
cd docs && python3 -m http.server 8765
```
