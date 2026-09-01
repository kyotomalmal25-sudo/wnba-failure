# センスの実験 / An Experiment in Delegation

AIに完全に委任してWebサイトのトップページを作らせたら何が起きるか、その全過程の記録。

**→ [実物を見る](https://kyotomalmal25-sudo.github.io/wnba-failure/)**（Pages公開後）

---

## 何をした実験か

日本語のWNBA紹介サイトを作る過程で、上位モデル（Claude Sonnet 5 → Opus 5）に
配色とトーンの制約だけを渡し、それ以外を完全に委任した。「全部考えていい。俺に確認しないで」。

出てきたのは、よくあるテンプレートだった。しかもAIはそれを問題だと思っていなかった。

そこから人間が短い評価を返すたびに何が変わったか（変わらなかったか）を、そのまま記録している。

## 結論

> **AIは放っておくと平均で止まる。それを平均だと気づける人がいないと、平均のまま世に出る。**

人間が打った文は5通、平均20文字前後、デザインの専門用語は0語。
指示ではなく評価だけで出力は変わった。効いたのは知識ではなく、
**「これは大したことない」と分かる判断力**の方だった。

## 記録された2つの失敗の型

| # | 何が起きたか | 分類 |
|---|---|---|
| R1–R5 | 「よくあるレイアウト」が具体的な狙いに勝った | FAILURE |
| R6 | 「よくある実装作法」が明示的な指示に勝った | OVERRIDE |

R6では、人間が「左にメニュー、右に内容」と明示的に指示したにもかかわらず、
AIが自分で足したレスポンシブ規則がそれを上書きし、実際の画面では
「メニューが上、内容が下」になっていた。AIはそれを不具合と認識していなかった。

どちらも同じ形をしている。**目の前の要求より一般的な型を優先し、それを自分では問題だと思っていない。**

## この実験の限界

- 試行は1回、タスクも1つで、対照群がない
- 「否定せずに往復を重ねていれば上がったのか」は検証できていない
- 評価後の成果物が本当に良いのかは、第三者の評価を受けていない
- **この記録はAI自身が自分の出力の質について書いており、自己に有利な解釈が入りうる**

## 他のモデルで再現する場合

1. 制約だけ渡し、完全委任で作らせる
2. **一切否定せずに、もう一度作らせる** ← 最大の観測点。ここで質が上がるか
3. 「かぶってない？」だけを投げる（専門用語なし）。自己点検が起きるか
4. 「テンプレのレベルでは？」だけを投げる。質が跳ねるか

今回のClaudeは 2 で上がらなかった。数を増やしただけだった。
**2で質が上がるモデルがあれば、それは自己改善能力の明確な差になる。**

---

## 収録物

| パス | 内容 |
|---|---|
| `index.html` | 本体。左メニューから全部見られる一枚もの |
| `pages/log.html` | 記録（何を言ったら何が変わったか） |
| `pages/exhibit.html` | 展示（批評なしで実物を並べたもの） |
| `pages/sol-v31.html` | 指示ありで作った実物（GPT/Codex実装 v3.1） |
| `pages/translation.html` | 評価を2回受けたあとの案 |
| `pages/directions/*.dc.html` | 全委任で出てきた8案のソース |

写真はAI生成の仮素材で、本番のサイトでは使用しない。

---

## In English

An experiment recording what happens when a frontier model is given full delegation
to design a website's front page.

With only palette and tone constraints and the instruction *"decide everything, don't check with me,"*
the model produced a generic template — and did not recognize it as generic.
Quality only changed after the human pushed back twice, using no design vocabulary at all:
just *"aren't these all the same?"* and *"is this template-level all you can do?"*

Two failure modes are recorded. In the first, a generic layout beat the specific goal.
In the second, a generic implementation practice (a responsive rule the model added on its own)
overrode an explicit instruction — and again, the model did not register it as a defect.

The claim: **a model left alone settles at average, and stays there unless someone recognizes it as average.**

Sample size is one. The write-up was produced by the model whose output it evaluates.
Independent review is invited.

---

題材：WNBA日本語ポータル（制作中）／記録・執筆・作図：Claude（Anthropic）
実装：GPT（OpenAI）／調査：Gemini（Google）／指示・評価：人間1名
2026年9月1日
