# Northstar MSP IT Support Lab

一个面向 Junior IT Support / Service Desk / MSP 岗位的实战作品集项目。项目模拟 Northstar Managed IT Services 为 20 人客户 MapleWorks Professional Services 提供身份、终端、文件、Microsoft 365、远程支持、工单和基础安全支持。

## 当前状态

**阶段 1：进行中。DC01、Forest/Domain、内部 DNS 与 DHCP 服务器端配置已完成并通过命令验证；OU、用户、组和 Windows 11 客户端仍待实施。最后更新：2026-07-18。**

本仓库严格区分计划与已验证结果：

- `[Planned]`：尚未实施
- `[Built]`：已经配置，但尚未完整验收
- `[Validated]`：已按验收步骤复测，并保存证据
- `[Troubleshot]`：通过工单完成故障复现、诊断、修复和用户确认

在真正完成验证前，不把计划写成简历成果。

## 业务场景

- MSP：Northstar Managed IT Services
- 客户：MapleWorks Professional Services
- 用户：20 人，分属 HR、Finance、Sales、Operations
- 办公模式：1 个办公室、3 名远程员工
- 核心服务：Windows Server AD DS、DNS、DHCP、文件共享、Windows 11、Microsoft 365、VPN、工单、Endpoint Security
- 测试域：`corp.northstar.test`

## 实施顺序

1. AD、DNS、DHCP、OU、用户、组、Windows 11 入域
2. FS01、部门共享、NTFS 权限、GPO、终端标准化
3. 工单系统、SLA、升级矩阵、知识库
4. Microsoft 365、Entra ID、MFA、Outlook、Teams、OneDrive、远程办公
5. 随机故障注入与 30 张完整工单
6. PowerShell 自动化、统计、最终报告和演示

详细路线见 [PROJECT-PLAN.md](PROJECT-PLAN.md)。当前开工文件是 [phase-1-runbook.md](active-directory/phase-1-runbook.md)。

当前状态见 [progress/CURRENT-STATUS.md](progress/CURRENT-STATUS.md)；按日期的最新记录见 [progress/2026-07-18-progress-log.md](progress/2026-07-18-progress-log.md)。

## 目录

- `architecture/`：逻辑架构、IP 规划、资产清单
- `active-directory/`：OU、组、GPO 与第一阶段实施记录
- `data/`：虚构用户数据
- `service-desk/`：SLA、工单模板、升级流程与样例工单
- `knowledge-base/`：知识库模板和成品文章
- `powershell/`：经验证的自动化脚本
- `incidents/`：需要升级的安全事件记录
- `evidence/`：脱敏截图、命令输出和验收证据（按阶段保存）
- `final-report/`：最终报告源文件与导出成品
- `progress/`：当前状态和按日期记录的实施日志
- `cases/`：每个故障 Case 的记录、选图和 LinkedIn 素材
- `linkedin/`：阶段性 LinkedIn 更新草稿

## 安全与隐私

禁止提交真实密码、恢复密钥、Token、API Key、个人信息、未脱敏截图或真实企业配置。虚拟用户均为虚构数据；临时密码不得写入 CSV、工单或截图。
