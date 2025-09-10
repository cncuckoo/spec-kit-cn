---
名称：plan
描述："规划如何实现指定功能。这是规范驱动开发流程的第二步。"
---

规划如何实现指定功能。

这是规范驱动开发（Spec-Driven Development）流程的第二步。

根据作为参数提供的实现细节，执行以下操作：

1. 在仓库根目录运行 `scripts/setup-plan.sh --json`，解析 JSON 输出，获取 FEATURE_SPEC、IMPL_PLAN、SPECS_DIR、BRANCH。后续所有文件路径均需为绝对路径。
2. 阅读并分析功能规范，理解：
   - 功能需求与用户故事
   - 功能性与非功能性要求
   - 成功标准与验收标准
   - 所有提及的技术约束或依赖

3. 阅读 `/memory/constitution.md`，明确宪章要求。

4. 执行实现方案模板：
   - 加载 `/templates/plan-template.md`（已复制到 IMPL_PLAN 路径）
   - 设置输入路径为 FEATURE_SPEC
   - 按模板主流程（Execution Flow）步骤1-10执行
   - 模板自洽且可直接执行
   - 按模板要求处理错误与检查门槛
   - 由模板引导，在 $SPECS_DIR 生成相关产物：
     * 第0阶段生成 research.md
     * 第1阶段生成 data-model.md、contracts/、quickstart.md
     * 第2阶段生成 tasks.md
   - 将参数中的用户细节补充到 Technical Context
   - 每完成一个阶段，及时更新进度追踪

5. 验证执行结果：
   - 检查进度追踪，确保所有阶段已完成
   - 确认所有必需产物均已生成
   - 保证执行过程中无 ERROR 状态

6. 报告结果，包括分支名称、文件路径及生成的所有产物。

所有文件操作均需使用以仓库根目录为基准的绝对路径，避免路径错误。