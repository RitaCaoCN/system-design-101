# Translation Next Study Discussion Checklist

- id: scope_anchor
  question: "本次翻译与计划是否仅覆盖下一阶段学习路线相关文档？"
  depends_on: []
  status: answered
  answer: "是。用户要求把相关文档翻译成中文到 translations/，并把这些文件作为待办项目添加到 docs/plans/。"
  design_trace:
    - "Scope"
    - "Plan Tasks"

- id: related_topic
  question: "“相关文档”具体指哪一组主题？"
  depends_on: []
  status: answered
  answer: "用户明确要求先翻译完“缓存与性能”和“数据库与存储”两组内容。"
  spec_gap_tags:
    - acceptance
  design_trace:
    - "Scope"
    - "Plan Tasks"

- id: delivery_mode
  question: "这次是否要直接翻译文档内容，还是先只创建待办计划与文件清单？"
  depends_on: []
  status: answered
  answer: "直接翻译文档内容，同时把这些文件作为待办项目添加到 docs/plans/。"
  spec_gap_tags:
    - acceptance
  design_trace:
    - "Execution"
    - "Acceptance"

- id: batch_size
  question: "如果直接翻译，第一批希望包含多少篇文档？"
  depends_on:
    - delivery_mode
  status: answered
  answer: "用户没有单独限定批次大小，当前执行假设为覆盖这两个分类下全部缺失中文翻译文件。"
  spec_gap_tags:
    - backpressure
  design_trace:
    - "Execution"

- id: directory_convention
  question: "新翻译文件是否继续沿用 translations/zh/*.zh.md 的命名方式？"
  depends_on: []
  status: answered
  answer: "从现有仓库结构看，中文翻译文件统一放在 translations/zh/，文件名以 .zh.md 结尾。"
  design_trace:
    - "File Layout"

- id: source_selection
  question: "相关文档是否以此前建议的缓存/性能、数据库/存储、软件架构三条主线为准？"
  depends_on:
    - related_topic
  status: answered
  answer: "以缓存与性能、数据库与存储两条主线为准；软件架构暂不在本次范围内。"
  spec_gap_tags:
    - doc_precedence
  design_trace:
    - "Scope"

- id: plan_shape
  question: "docs/plans/ 中的待办计划是只列文件清单，还是包含翻译顺序、验收标准和逐步任务？"
  depends_on: []
  status: answered
  answer: "需要作为待办项目添加到 docs/plans/，因此计划应包含文件清单、翻译顺序、执行任务和验收标准。"
  spec_gap_tags:
    - acceptance
  design_trace:
    - "Plan Tasks"
    - "Acceptance"
