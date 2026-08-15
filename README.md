# finance-books

独立 git repo, 管理 evening_study 每日学习的书本内容.

## 结构

```
finance-books/
├── permanent-portfolio/
│   ├── README.md (章节笔记)
│   └── principles.json (结构化原则, 供 evening_study.py 抽取)
├── antifragile/
│   └── principles.json
└── buffett-letters/
    └── principles.json
```

## 接入方式

finance-stack 通过 git submodule 接入:

```bash
cd ~/projects/finance-stack
git submodule add git@github.com:JacobYeh/finance-books.git skills/finance-advisor/memory/books
```

## 编辑流程

1. 在本 repo 修改原则或笔记
2. `git commit -m "..." && git push origin master`
3. 在 finance-stack 端 `git submodule update --remote` 拉取最新

## 原则 schema

`principles.json` 每条原则:
```json
{
  "id": "BUF-06",
  "name": "低费率指数基金最优",
  "summary": "...",
  "trigger_keywords": ["费率", "指数"],
  "holding_signal": "持仓费率 > 0.5% → 考虑替换更便宜的同类"
}
```
