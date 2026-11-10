---
name: 公募基金规模统计
description: 用两份公募季报 Excel 生成九分类/非货规模统计与排名台账（规则修订版，支持季报内 ETF 穿透列）。用户说公募规模统计、非货排名、季报台账、规则修订规模表时使用。
agent_created: true
---

# 公募基金规模统计

同事给出**当期 + 上期**两份季报 Excel 时，运行本技能 `run_stats.py`，把打印的 `FILE=` 路径发给对方。

优先用季报末列穿透（如「持有基金市值占比」）算联接残差；没有则回退约 7% 类型默认残差。

## 怎么运行

```bash
/usr/local/bin/python3 -m pip install -r "${CODEBUDDY_SKILL_DIR}/requirements.txt"
```

指定两份文件（推荐）：

```bash
/usr/local/bin/python3 "${CODEBUDDY_SKILL_DIR}/run_stats.py" \
  "/路径/当期季报.xlsx" "/路径/上期季报.xlsx"
```

若另有 ETF 联接穿透持仓占比表：

```bash
/usr/local/bin/python3 "${CODEBUDDY_SKILL_DIR}/run_stats.py" \
  "/路径/当期季报.xlsx" "/路径/上期季报.xlsx" \
  --link-holdings "/路径/ETF联接持仓占比.xlsx"
```

或把两份最新季报放进一个目录后自动找：

```bash
/usr/local/bin/python3 "${CODEBUDDY_SKILL_DIR}/run_stats.py" --input-dir "/路径/季报目录"
```

默认输出到 `${CODEBUDDY_SKILL_DIR}/输出/`。

## 对话流程

1. 向同事要当期、上期季报；可选再要 ETF 穿透持仓占比表。
2. 跑上面的命令；不要改分类规则。
3. 把 `FILE=` 结果发给同事。

## 网页版

打开：https://zylugarry-lab.github.io/fund-aum-stats/

上传当期+上期季报，可选再传 ETF 穿透持仓占比，浏览器内生成台账（Pyodide）。
