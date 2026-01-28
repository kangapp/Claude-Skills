---
name: writing-plans
description: 当你有多步骤任务的规格说明或需求时，在接触代码之前使用
---

# 编写计划

## 概述

编写全面的实施计划，假设工程师对代码库零上下文，且品味存疑。记录他们需要了解的一切：每个任务要修改哪些文件、代码、测试、可能需要检查的文档、如何测试。将整个计划分解为 bite-sized 任务。DRY、YAGNI、TDD。

假设他们是熟练的开发者，但几乎不了解我们的工具集或问题领域。假设他们不太了解良好的测试设计。

**开始时宣布：\"我正在使用 writing-plans 技能来创建实施计划。\"**

**上下文：** 这应该在专用的工作树中运行（由 brainstorming 技能创建）。

**保存计划到：** `docs/plans/YYYY-MM-DD-<feature-name>.md`

## 小任务粒度

**每个步骤是一个动作（2-5 分钟）：**
- \"编写失败的测试\" - 步骤
- \"运行以确保它失败\" - 步骤
- \"实现使测试通过的最小代码\" - 步骤
- \"运行测试并确保它们通过\" - 步骤

## 计划文档头部

**每个计划必须以这个头部开始：**

```markdown
# [功能名称] 实施计划

**目标：** [一句话描述这将构建什么]

**架构：** [2-3 句关于方法的描述]

**技术栈：** [关键技术/库]

---
```

## 任务结构

```markdown
### 任务 N: [组件名称]

**文件：**
- 创建: `exact/path/to/file.py`
- 修改: `exact/path/to/existing.py:123-145`
- 测试: `tests/exact/path/to/test.py`

**步骤 1: 编写失败的测试**

```python
def test_specific_behavior():
    result = function(input)
    assert result == expected
```

**步骤 2: 运行测试以验证它失败**

运行: `pytest tests/path/test.py::test_name -v`
预期: FAIL，显示 \"function not defined\"

**步骤 3: 编写最小实现**

```python
def function(input):
    return expected
```

**步骤 4: 运行测试以验证它通过**

运行: `pytest tests/path/test.py::test_name -v`
预期: PASS

```

## 记住
- 始终使用精确的文件路径
- 计划中的完整代码（不是 \"添加验证\"）
- 精确的命令和预期输出
- 使用 @ 语法引用相关技能
- DRY、YAGNI、TDD

