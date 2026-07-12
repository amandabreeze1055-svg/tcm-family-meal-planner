# TCM Family Meal Planner

`tcm-family-meal-planner` is an evidence-bounded Skill for planning Chinese dietary-wellness meals for families.

It starts with a household interview, builds a confirmed food-and-recipe profile, and then plans meals from family preferences, allergies, ages, available ingredients, cooking constraints, and the companion Web App's governed content and deterministic meal rules.

中文说明：这是一个面向家庭的中式食养整餐规划 Skill。它先采访家庭成员、年龄、体质自述、过敏、口味和常做菜，再根据可追溯的项目资料与确定性规则规划一餐或多日计划。

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
