# Univer 前端独立部署分析 / Frontend-Only Deployment Analysis

## 问题分析 / Problem Statement

本文档分析 Univer 项目是否支持不部署后端，仅依赖前端来实现表格文件的编辑功能。

This document analyzes whether the Univer project supports frontend-only deployment without a backend for spreadsheet editing functionality.

---

## 结论 / Conclusion

**✅ 是的，Univer 支持纯前端部署和使用**

**✅ Yes, Univer supports frontend-only deployment and usage**

Univer 采用**同构架构**（Isomorphic Architecture），核心功能设计为可以在浏览器和 Node.js 环境中运行。大部分基础功能都可以在纯前端环境下工作，无需后端服务器。

Univer uses an **Isomorphic Architecture**, with core features designed to run in both browser and Node.js environments. Most basic features can work in a pure frontend environment without a backend server.

---

## 详细分析 / Detailed Analysis

### 1. 架构设计 / Architecture Design

Univer 的架构遵循以下原则：

- **同构设计**：支持浏览器和 Node.js 环境
- **插件化架构**：功能通过插件加载，可按需使用
- **UI 与逻辑分离**：底层逻辑（models, commands, mutations）与 UI 层（React 组件、菜单等）分离

Univer's architecture follows these principles:

- **Isomorphic Design**: Supports both browser and Node.js environments
- **Plugin Architecture**: Features are loaded via plugins, can be used as needed
- **Separation of UI and Logic**: Core logic (models, commands, mutations) is separated from UI layer (React components, menus, etc.)

参考文档：[ISOMOPHIC.md](./ISOMOPHIC.md)

### 2. 开源版本（OSS）前端可用功能 / OSS Frontend-Available Features

以下功能在开源版本中提供，可以完全在前端运行：

The following features are available in the OSS version and can run entirely in the frontend:

#### 📊 Univer Sheets 核心功能 / Core Features

- ✅ **核心功能** / **Core Features**: 单元格、行、列、工作表、工作簿
  - Cells, rows, columns, worksheets, and workbooks
- ✅ **公式计算** / **Formulas**: 数学、统计、逻辑、文本、日期时间等各类公式
  - Mathematical, statistical, logical, text, date and time formulas
  - 支持 Web Worker 异步计算 / Supports Web Worker async computation
- ✅ **权限控制** / **Permissions**: 限制访问特定元素
  - Restrict access to specific elements
- ✅ **数字格式化** / **Number Formatting**: 根据条件格式化数字
  - Format numbers based on specific criteria
- ✅ **超链接** / **Hyperlinks**: 链接到外部网站、邮箱等
  - Link to external websites, email addresses
- ✅ **浮动图片** / **Floating Images**: 插入和定位图片
  - Insert and position images
- ✅ **查找和替换** / **Find & Replace**: 搜索和替换文本
  - Search and replace text
- ✅ **筛选** / **Filtering**: 根据条件筛选数据
  - Filter data based on criteria
- ✅ **排序** / **Sorting**: 数据排序
  - Sort data
- ✅ **数据验证** / **Data Validation**: 限制单元格数据类型
  - Restrict cell data types
- ✅ **条件格式** / **Conditional Formatting**: 基于条件应用格式
  - Apply formatting based on criteria
- ✅ **评论/批注** / **Comments/Notes**: 添加单元格评论
  - Add cell comments
- ✅ **十字高亮** / **Cross-highlighting**: 选中单元格的十字高亮
  - Cross-highlighting for selected cells
- ✅ **禅模式编辑器** / **Zen Editor**: 无干扰编辑体验
  - Distraction-free editing experience
- ✅ **表格** / **Tables**: 表格功能
  - Table functionality
- ✅ **主题定制** / **Theme Customization**: 自定义外观
  - Customize appearance
- ✅ **国际化** / **Internationalization**: 多语言支持
  - Multi-language support

#### 📝 Univer Docs 核心功能 / Core Features

- ✅ **核心功能** / **Core Features**: 段落、标题、列表、上下标等
  - Paragraphs, headings, lists, superscript, subscript
- ✅ **列表** / **Lists**: 有序列表、无序列表、任务列表
  - Ordered lists, unordered lists, task lists
- ✅ **超链接** / **Hyperlinks**: 插入链接
  - Insert links
- ✅ **浮动图片** / **Floating Images**: 图文混排
  - Text and image layout
- ✅ **页眉页脚** / **Headers & Footers**: 添加页眉页脚
  - Add headers and footers
- ✅ **评论** / **Comments**: 添加评论
  - Add comments

#### 🔧 其他能力 / Other Capabilities

- ✅ **CSV 导入** / **CSV Import**: 可以通过前端代码实现（参见示例）
  - Can be implemented via frontend code (see examples)
- ✅ **本地文件读写** / **Local File I/O**: 通过浏览器 File API
  - Via browser File API
- ✅ **Web Worker 支持** / **Web Worker Support**: 公式计算可在 Worker 中运行
  - Formula computation can run in Worker threads
- ✅ **撤销/重做** / **Undo/Redo**: 完整的历史记录管理
  - Complete history management
- ✅ **复制/粘贴** / **Copy/Paste**: 剪贴板操作
  - Clipboard operations

### 3. 非开源版本（Pro）功能 / Non-OSS (Pro) Features

以下功能需要 Univer 的非开源版本[^1]，这些功能可能需要后端支持：

The following features require the non-OSS version of Univer[^1], and may require backend support:

- ❌ **协同编辑** / **Collaborative Editing**: 多用户实时协作
  - Real-time multi-user collaboration
- ❌ **导入导出 XLSX** / **Import & Export XLSX**: 完整的 Excel 文件支持
  - Full Excel file support
- ❌ **导入导出 DOCX** / **Import & Export DOCX**: 完整的 Word 文件支持
  - Full Word file support
- ❌ **打印和 PDF 导出** / **Printing & PDF Export**: 打印和 PDF 生成
  - Printing and PDF generation
- ❌ **图表** / **Charts**: 各类图表（柱状图、折线图、饼图等）
  - Various charts (bar, line, pie, etc.)
- ❌ **数据透视表** / **Pivot Tables**: 数据汇总分析
  - Data summarization and analysis
- ❌ **迷你图** / **Sparklines**: 单元格内的小型图表
  - Small charts within cells
- ❌ **编辑历史** / **Editing History**: 版本历史和恢复
  - Version history and recovery

**注意 / Note**: 这些功能在非开源版本中可**免费用于商业用途**，也提供付费升级计划。
These features are **free for commercial use** in the non-OSS version, with paid upgrade plans available.

[^1]: 详见 README 中的说明 / See README for details

### 4. 前端独立部署示例 / Frontend-Only Deployment Example

项目中已经提供了完整的前端示例，展示如何在纯前端环境中使用 Univer：

The project provides complete frontend examples showing how to use Univer in a pure frontend environment:

**示例路径 / Example Path**: `/examples/src/sheets/main.ts`

**关键特性 / Key Features**:
- 无后端依赖 / No backend dependencies
- 本地运行 / Runs locally
- 完整的编辑功能 / Full editing capabilities
- CSV 导入示例 / CSV import example (`/examples/src/sheets/custom/import-csv-button.ts`)

**运行方式 / How to Run**:
```bash
pnpm install
pnpm dev
```

这将启动一个本地开发服务器，完全在浏览器中运行，无需任何后端服务。

This starts a local development server that runs entirely in the browser without any backend services.

### 5. 网络和协同功能 / Network and Collaboration Features

- **`@univerjs/network`** 包主要用于**协同编辑场景**
  - The `@univerjs/network` package is primarily for **collaborative editing scenarios**
- **`@univerjs/rpc`** 用于 Web Worker 通信，不是后端通信
  - The `@univerjs/rpc` is for Web Worker communication, not backend communication
- **`@univerjs/rpc-node`** 用于 Node.js 环境，但不是必需的
  - The `@univerjs/rpc-node` is for Node.js environments but not required

**对于纯前端使用，这些包是可选的。**

**For pure frontend use, these packages are optional.**

### 6. 数据持久化 / Data Persistence

在纯前端部署中，数据持久化可以通过以下方式实现：

In frontend-only deployment, data persistence can be achieved through:

1. **LocalStorage / IndexedDB**: 浏览器本地存储
   - Browser local storage
2. **文件下载/上传** / **File Download/Upload**: 通过 File API
   - Via File API
3. **JSON 序列化** / **JSON Serialization**: Univer 数据模型可序列化为 JSON
   - Univer data models can be serialized to JSON
4. **CSV 导入导出** / **CSV Import/Export**: 示例代码已提供
   - Example code provided

---

## 使用建议 / Recommendations

### ✅ 适合前端独立部署的场景 / Suitable for Frontend-Only Deployment

1. **单用户编辑** / **Single-user editing**: 个人使用或本地编辑
2. **离线应用** / **Offline applications**: 不需要服务器的场景
3. **轻量级集成** / **Lightweight integration**: 嵌入到现有前端应用
4. **数据可视化** / **Data visualization**: 展示和简单编辑
5. **原型开发** / **Prototyping**: 快速原型验证

### ❌ 不适合前端独立部署的场景 / Not Suitable for Frontend-Only Deployment

1. **多用户协同** / **Multi-user collaboration**: 需要实时同步
2. **复杂文件格式** / **Complex file formats**: 需要完整的 XLSX/DOCX 支持
3. **服务端计算** / **Server-side computation**: 大规模数据计算
4. **版本控制** / **Version control**: 完整的历史记录和恢复

---

## 总结 / Summary

Univer 的开源版本**完全支持前端独立部署**，提供了丰富的电子表格和文档编辑功能。对于大多数基础编辑需求，不需要后端服务器即可使用。

The OSS version of Univer **fully supports frontend-only deployment** with rich spreadsheet and document editing features. For most basic editing needs, no backend server is required.

如果需要协同编辑、完整的 Office 文件导入导出、打印等高级功能，则需要使用 Univer 的非开源版本（Pro），这些功能可能需要后端支持。

If you need advanced features like collaborative editing, full Office file import/export, or printing, you'll need the non-OSS version (Pro) of Univer, which may require backend support.

---

## 参考资源 / References

- [README.md](../README.md) - 项目介绍和特性列表 / Project introduction and features
- [README-zh.md](../README-zh.md) - 中文版项目介绍 / Chinese version
- [ISOMOPHIC.md](./ISOMOPHIC.md) - 同构架构说明 / Isomorphic architecture
- [官方文档 / Official Documentation](https://docs.univer.ai)
- [在线示例 / Online Examples](https://docs.univer.ai/showcase)
- [Univer Presets Repository](https://github.com/dream-num/univer-presets) - 预设配置 / Preset configurations

---

## 快速开始示例代码 / Quick Start Example Code

```typescript
import { Univer, UniverInstanceType } from '@univerjs/core';
import { UniverDocsPlugin } from '@univerjs/docs';
import { UniverDocsUIPlugin } from '@univerjs/docs-ui';
import { UniverFormulaEnginePlugin } from '@univerjs/engine-formula';
import { UniverRenderEnginePlugin } from '@univerjs/engine-render';
import { UniverSheetsPlugin } from '@univerjs/sheets';
import { UniverSheetsFormulaPlugin } from '@univerjs/sheets-formula';
import { UniverSheetsUIPlugin } from '@univerjs/sheets-ui';
import { UniverUIPlugin } from '@univerjs/ui';

// 创建 Univer 实例 / Create Univer instance
const univer = new Univer({
    locale: 'zh-CN',
});

// 注册插件 / Register plugins
univer.registerPlugins([
    UniverDocsPlugin,
    UniverRenderEnginePlugin,
    UniverUIPlugin,
    UniverDocsUIPlugin,
    UniverSheetsPlugin,
    UniverSheetsUIPlugin,
    UniverFormulaEnginePlugin,
    UniverSheetsFormulaPlugin,
]);

// 创建工作簿 / Create workbook
univer.createUnit(UniverInstanceType.UNIVER_SHEET, {
    id: 'workbook-01',
    name: 'My Workbook',
    sheets: {
        'sheet-01': {
            id: 'sheet-01',
            name: 'Sheet1',
            cellData: {
                0: {
                    0: { v: 'Hello' },
                    1: { v: 'Univer' },
                },
            },
        },
    },
});
```

这个示例展示了如何在纯前端环境中初始化 Univer，无需任何后端服务。

This example shows how to initialize Univer in a pure frontend environment without any backend services.

---

**创建时间 / Created**: 2025-12-19
**版本 / Version**: Based on Univer v0.13.0
