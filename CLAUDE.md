# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This repository contains Japanese-language documentation for an internal operations improvement project (ex-ops-improvement) focused on streamlining helpdesk and IT support operations. The project aims to reduce dependency on specific personnel and improve response times through standardized workflows and automation.

## Project Structure

### Core Documentation Areas

- **[docs/業務体制の整備.md](docs/業務体制の整備.md)**: Main project definition and objectives
  - Project goal: Achieve 60%+ of helpdesk responses processed through defined systems rather than ad-hoc
  - Two main sub-projects: ① Business scope/structure/personnel clarification and ② Reporting line construction
  - Contains task breakdowns, time estimates (48 hours total / 6 person-days), and phased implementation steps

- **[docs/対応体制の構築・フローの整備と自動化.md](docs/対応体制の構築・フローの整備と自動化.md)**: Response system construction and automation
  - Step 1: Response structure construction (Doer/Supporter rotation system)
  - Step 2: Request response flow arrangement and automation design (Slack forms, bot-based triage, Notion integration)
  - Step 3: Business efficiency and automation opportunities

- **[docs/レポートラインの構築.md](docs/レポートラインの構築.md)**: Reporting line construction specifics
  - Defines reportable events, templates, case-based flows, and trial operations

### Sub-directory: 対応体制の構築・フローの整備と自動化/

- **[サブカテゴリごとのヒアリングテンプレートの作成.md](docs/対応体制の構築・フローの整備と自動化/サブカテゴリごとのヒアリングテンプレートの作成.md)**: Hearing template design
  - Slack form design with 6 request categories (hardware, network, accounts, internal systems, security)
  - Notion DB field mapping and priority scoring algorithm
  - Zapier/Slack Workflow Builder integration specs

- **[ヘルプデスク業務棚卸.md](docs/対応体制の構築・フローの整備と自動化/ヘルプデスク業務棚卸.md)**: Complete helpdesk task inventory
  - Comprehensive table of 40+ task types with domain assignments (EX, 基盤, 開発, セキュリティ)
  - Each task includes: sub-category, priority, immediate response flag, assigned personnel, supporting roles, responsible parties, and decision makers

- **[system-requestへのヒアリング設計.md](docs/対応体制の構築・フローの整備と自動化/system-requestへのヒアリング設計.md)**: system-request channel hearing design
  - Integration of templates with generative AI for faster triage and response detection

## Key Architecture Concepts

### 1. Four Domain Structure
Operations are divided across four domains with designated personnel:
- **EX (Employee Experience)**: End-user support, software installation, hardware provisioning
- **基盤 (Infrastructure)**: Network, VPN, hardware setup, air conditioning systems
- **開発 (Development)**: Internal system bugs, feature requests, data investigation
- **セキュリティ (Security)**: Security incidents, phishing, access anomalies

### 2. Role Hierarchy
- **担当者 (Assignee)**: Primary responder
- **補佐 (Supporter)**: Backup support team
- **責任者 (Responsible Party)**: Domain lead
- **判断者 (Decision Maker)**: Final authority (typically Yuichiro Inoue or Shunnosuke Sumi)

### 3. Priority Calculation Algorithm
Priority scores are auto-calculated based on:
- **Impact scope** (全社/部門/個人): 3/2/1 × weight 2
- **Desired timeline** (ASAP/今週中/指定日): 3/2/1 × weight 1.5
- **Request type** (障害/設定変更/要望): 3/2/1 × weight 1

Score ranges:
- 8+ points: 🔴 Urgent
- 5-7 points: 🟡 Normal
- ≤4 points: 🟢 Low

### 4. Automation Flow
```
Slack form submission → Workflow Builder/Zapier trigger →
JSON conversion → Notion API POST →
Notion DB record creation → Priority auto-calculation →
Domain/assignee notification
```

## Working with This Repository

### Documentation Language
All documentation is in Japanese. When editing or creating new documents:
- Maintain consistent Japanese business writing style
- Use markdown tables for structured data
- Follow the existing heading hierarchy conventions
- Preserve the Notion link format: `[Link text](https://www.notion.so/...)`

### Adding New Tasks
When adding tasks to [ヘルプデスク業務棚卸.md](docs/対応体制の構築・フローの整備と自動化/ヘルプデスク業務棚卸.md):
1. Include all columns: ドメイン, 分類, サブカテゴリ, 業務, タスク例, 即時対応, 優先度, 担当者, 補佐, 責任者, 判断者
2. Align with the six main request categories
3. Ensure domain assignment matches personnel capabilities

### Project Status References
The project uses Notion extensively for tracking. References to Notion pages are intentionally preserved as they represent the live project management environment.

## File Organization Principles

- Top-level docs for high-level project definitions and cross-cutting concerns
- Sub-directories for detailed implementation specifications related to specific phases
- No source code exists in this repository—it is purely documentation-driven
