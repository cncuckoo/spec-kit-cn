# 文件信息

- 原始文件：tasks-template.md
- 翻译时间：2025/09/10 11:16:26

---

# 任务：[功能名称]

**输入**：来自 `/specs/[###-feature-name]/` 的设计文档  
**前置条件**：plan.md（必需），research.md，data-model.md，contracts/

## 执行流程（主流程）
```
1. 从功能目录加载 plan.md
   → 若未找到：报错 "未找到实现计划"
   → 提取：技术栈、依赖库、结构
2. 加载可选设计文档：
   → data-model.md：提取实体 → 建模任务
   → contracts/：每个文件 → 合约测试任务
   → research.md：提取决策 → 初始化任务
3. 按类别生成任务：
   → 初始化：项目结构、依赖、代码规范
   → 测试：合约测试、集成测试
   → 核心：模型、服务、CLI 命令
   → 集成：数据库、中间件、日志
   → 优化：单元测试、性能、文档
4. 应用任务规则：
   → 不同文件 = 标记 [P] 可并行
   → 同一文件 = 顺序执行（不标 [P]）
   → 测试优先于实现（TDD）
5. 任务编号顺序排列（T001, T002...）
6. 生成依赖关系图
7. 给出并行执行示例
8. 校验任务完整性：
   → 所有合约均有测试？
   → 所有实体均有模型？
   → 所有接口均已实现？
9. 返回：SUCCESS（任务可执行）
```

## 格式：`[ID] [P?] 描述`
- **[P]**：可并行执行（不同文件、无依赖）
- 描述中需包含精确文件路径

## 路径约定
- **单项目**：`src/`、`tests/` 位于仓库根目录
- **Web 应用**：`backend/src/`、`frontend/src/`
- **移动端**：`api/src/`、`ios/src/` 或 `android/src/`
- 下述路径以单项目为例，具体以 plan.md 结构为准

## 阶段 3.1：初始化
- [ ] T001 按实现计划创建项目结构
- [ ] T002 使用 [语言] 初始化项目并添加 [框架] 依赖
- [ ] T003 [P] 配置代码规范和格式化工具

## 阶段 3.2：测试优先（TDD）⚠️ 必须在 3.3 前完成
**关键：这些测试必须先写且必须先失败，之后才能进行实现**
- [ ] T004 [P] 在 tests/contract/test_users_post.py 编写 POST /api/users 合约测试
- [ ] T005 [P] 在 tests/contract/test_users_get.py 编写 GET /api/users/{id} 合约测试
- [ ] T006 [P] 在 tests/integration/test_registration.py 编写用户注册集成测试
- [ ] T007 [P] 在 tests/integration/test_auth.py 编写认证流程集成测试

## 阶段 3.3：核心实现（仅在测试失败后进行）
- [ ] T008 [P] 在 src/models/user.py 实现用户模型
- [ ] T009 [P] 在 src/services/user_service.py 实现 UserService 的 CRUD
- [ ] T010 [P] 在 src/cli/user_commands.py 实现 CLI --create-user 命令
- [ ] T011 实现 POST /api/users 接口
- [ ] T012 实现 GET /api/users/{id} 接口
- [ ] T013 实现输入校验
- [ ] T014 实现错误处理与日志

## 阶段 3.4：集成
- [ ] T015 连接 UserService 与数据库
- [ ] T016 实现认证中间件
- [ ] T017 实现请求/响应日志
- [ ] T018 实现 CORS 与安全头

## 阶段 3.5：优化
- [ ] T019 [P] 在 tests/unit/test_validation.py 编写校验相关单元测试
- [ ] T020 性能测试（<200ms）
- [ ] T021 [P] 更新 docs/api.md 文档
- [ ] T022 移除重复代码
- [ ] T023 执行 manual-testing.md 手动测试

## 依赖关系
- 测试（T004-T007）必须先于实现（T008-T014）
- T008 阻塞 T009、T015
- T016 阻塞 T018
- 实现阶段必须先于优化阶段（T019-T023）

## 并行示例
```
# 同时启动 T004-T007：
任务：“在 tests/contract/test_users_post.py 中进行 POST /api/users 的契约测试”
任务：“在 tests/contract/test_users_get.py 中进行 GET /api/users/{id} 的契约测试”
任务：“在 tests/integration/test_registration.py 中进行注册集成测试”
任务：“在 tests/integration/test_auth.py 中进行认证集成测试”
```

## 说明
- [P] 任务 = 不同文件，无依赖关系
- 实现前需验证测试失败
- 每完成一个任务就提交一次
- 避免：任务描述模糊、同一文件冲突

## 任务生成规则
*在 main() 执行时应用*

1. **基于契约**：
   - 每个契约文件 → 一个契约测试任务 [P]
   - 每个接口 → 一个实现任务

2. **基于数据模型**：
   - 每个实体 → 一个模型创建任务 [P]
   - 关联关系 → 服务层任务

3. **基于用户故事**：
   - 每个故事 → 一个集成测试 [P]
   - 快速入门场景 → 校验任务

4. **任务顺序**：
   - 环境搭建 → 测试 → 模型 → 服务 → 接口 → 优化
   - 有依赖的任务不能并行执行

## 校验清单
*GATE：main() 返回前检查*

- [ ] 所有契约都有对应测试
- [ ] 所有实体都有模型任务
- [ ] 所有测试都在实现之前
- [ ] 并行任务真正独立
- [ ] 每个任务都明确指定文件路径
- [ ] 没有任务与其他 [P] 任务修改同一文件