# TCM Family Meal Planner

`tcm-family-meal-planner` is an evidence-bounded Skill for planning Chinese dietary-wellness meals for families.

It starts with a household interview, builds a confirmed food-and-recipe profile, and then plans meals from family preferences, allergies, ages, available ingredients, cooking constraints, and the companion Web App's governed content and deterministic meal rules.

中文说明：这是一个面向家庭的中式食养整餐规划 Skill。它先采访家庭成员、年龄、体质自述、过敏、口味和常做菜，再根据可追溯的项目资料与确定性规则规划一餐或多日计划。

## 什么是“食品配伍”和“配伍餐”？

食品配伍，是按照有出处的中医食养资料、家庭成员的实际情况、食材形态、烹调条件和一顿饭的结构，把几种食材或几道菜组织成一个有理由的家常组合。

配伍餐需要回答：

- 为什么把这些菜放在同一顿饭里？
- 这条理由属于中医食养依据、家庭适配、烹调关系，还是普通整餐结构？
- 哪些食材、形态、做法、人群和用量条件让这个理由成立？
- 哪些内容仍然缺少直接证据？

它用于日常饮食参考，内容不等同于中药方剂、诊断、处方或疾病治疗。五行标注只用于说明传统理论背景；五味、性味、归经、颜色和五行不能在没有来源时互相替代，也不能单独决定菜单。

没有直接组合证据时，Skill 会明确写“结构性搭配”或“直接组合证据尚未建立”，不会把普通菜谱组合包装成正式中医配伍。

## Invocation

```text
$tcm-family-meal-planner
```

Example:

```text
使用 $tcm-family-meal-planner，先建立我的家庭饮食档案，再根据今天的时间和库存规划晚餐。
```

## Scope

- Uses project-governed `SourceRef`, `SourcePassage`, `EvidenceLink`, `Ingredient`, `Recipe`, and constitution rules when the companion Web App is available.
- Uses deterministic whole-meal composition rules for roles, portions, time, difficulty, ingredient repetition, and shopping lists.
- Requires an evidence boundary for every TCM-related claim.
- Keeps `AI_DRAFT`, machine QA, human review, compliance approval, and activation as separate states.
- Stops when direct pairing evidence is unavailable instead of inventing a TCM pairing claim.
- Does not diagnose, prescribe, promise efficacy, or replace professional advice.

## Installation

Copy this repository directory into the local Skill directory used by your Agent:

```bash
cp -R tcm-family-meal-planner ~/.codex/skills/tcm-family-meal-planner
```

For OpenClaw or another Agent runtime, load the `SKILL.md` file and provide equivalent access to the companion Web App's approved read-only content API or governed content package. The Skill does not grant database, Web App, GitHub, or Apple Notes permissions by itself.

## Companion Web App contract

When the companion Web App is available, the preferred read-only resources are:

```text
GET /api/public/v1
GET /api/public/v1/ingredients
GET /api/public/v1/recipes
GET /api/public/v1/knowledge
GET /api/public/v1/openapi
```

The public API exposes approved, non-mock content only. It does not expose household health profiles or personalized plan writes. Demo content must remain visibly identified as demo or AI draft content.

## License

MIT. See [LICENSE](LICENSE).

## Safety boundary

This project is for daily dietary reference and meal planning. It is not a diagnostic, prescription, disease-treatment, or efficacy-guarantee system. Health and allergy information should remain in the user's authorized private context and should not be committed to this repository.
