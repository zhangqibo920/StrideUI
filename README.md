## 一、简介

StrideUI 是一套专为高效开发、优质体验打造的组件库，聚焦简洁易用与灵活拓展，助力开发者快速构建美观且交互流畅的界面，覆盖 Web 等多端场景，适配各类项目需求，让界面开发大步 “Stride” 向前。

## 二、核心优势

### （一）简洁易用

* **API 设计简洁**：组件调用逻辑清晰，参数少而精准，如按钮组件 `<StrideButton>` ，只需传入 `type`（按钮类型，如 `primary` / `default` ）、`onClick`（点击回调 ）等关键属性，即可快速渲染，降低学习成本。
* **文档直观友好**：配套文档提供详细示例、属性说明，每个组件都有可直接运行的代码片段，像表单组件文档里，从基础表单布局到复杂校验逻辑，一步一示例，开发者能快速照搬复用。

### （二）灵活拓展

* **主题定制**：支持深度主题配置，通过修改 `theme.config.js` ，可自定义色彩、圆角、阴影等样式变量，轻松适配企业品牌色，让组件风格与项目视觉体系高度统一。
* **组件扩展**：基于 Vue / React 等框架的组件扩展机制，可继承基础组件（如 `StrideInput` ），添加自定义校验、交互逻辑，像扩展验证码输入组件，复用输入框基础能力，快速叠加倒计时、验证码校验功能。

### （三）多端适配

* **响应式适配**：组件内置响应式逻辑，表格 `<StrideTable>` 在移动端自动适配为卡片流式布局，图表 `<StrideChart>` 随容器尺寸智能缩放，无需额外编写大量适配代码，适配 PC、平板、手机等多终端。
* **跨框架兼容（可选）**：若适配多技术栈，可通过封装，支持 Vue、React 等主流框架，一套设计逻辑，多框架复用，降低团队技术切换成本。

## 三、核心组件

### （一）基础组件

* **按钮（StrideButton）**：提供默认、主要、危险等多种预设类型，支持加载状态（传入 `loading` 属性显示加载动画 ）、禁用状态，满足交互反馈需求，代码示例：

vue

```
<StrideButton type="primary" :loading="isLoading" @click="handleClick">
  提交
</StrideButton>
```

* **输入框（StrideInput）**：包含文本、密码、搜索等类型，支持实时校验（绑定 `validator` 函数 ）、清空按钮（配置 `clearable` ），适配表单场景，示例：

react

```
<StrideInput 
  type="text" 
  placeholder="请输入内容" 
  validator={(value) => value.length > 0} 
  clearable 
  onChange={handleChange} 
/>
```

### （二）布局组件

* **栅格系统（StrideGrid）**：基于 24 分栏，通过 `Row` + `Col` 组合，快速实现页面布局，支持不同屏幕断点的列数调整，比如：

html

预览

```
<StrideRow>
  <StrideCol :span="8" :smSpan="12">左侧内容</StrideCol>
  <StrideCol :span="16" :smSpan="12">右侧内容</StrideCol>
</StrideRow>
```

* **布局容器（StrideLayout）**：包含 `Header`、`Content`、`Footer`、`Sider` ，用于构建后台管理系统等典型布局，可固定侧边栏、头部，示例：

vue

```
<StrideLayout>
  <StrideLayout.Sider width="200">侧边导航</StrideLayout.Sider>
  <StrideLayout.Content>页面主体</StrideLayout.Content>
</StrideLayout>
```

### （三）业务组件

* **表格（StrideTable）**：支持动态列配置、分页、排序、多选，可通过 `columns` 定义表头与数据映射，`dataSource` 传入表格数据，示例：

react

```
const columns = [
  { title: '姓名', dataIndex: 'name' },
  { title: '年龄', dataIndex: 'age', sorter: (a, b) => a.age - b.age }
];
<StrideTable columns={columns} dataSource={tableData} />
```

* **表单（StrideForm）**：联动 `StrideInput`、`StrideSelect` 等组件，实现表单校验、联动提交，通过 `formSchema` 配置表单项，示例：

vue

```
<StrideForm :formSchema="formSchema" @submit="handleSubmit">
  <template #username>
    <StrideInput placeholder="用户名" />
  </template>
  <template #password>
    <StrideInput type="password" placeholder="密码" />
  </template>
</StrideForm>
<script setup>
const formSchema = {
  username: { label: '用户名', required: true },
  password: { label: '密码', required: true }
};
</script>
```

## 四、快速上手

### （一）安装

#### npm 安装

bash

```
npm install stride-ui --save
```

#### yarn 安装

bash

```
yarn add stride-ui
```

### （二）引入使用（以 Vue 为例 ）

vue

```
<template>
  <StrideButton type="primary">Hello StrideUI</StrideButton>
</template>
<script setup>
import { StrideButton } from 'stride-ui';
</script>
<style>
/* 可引入组件库默认样式，或自定义主题样式 */
import 'stride-ui/dist/style.css'; 
</style>
```

## 五、适用场景

* **后台管理系统**：借助丰富的表格、表单、布局组件，快速搭建数据管理、权限配置等页面，提升开发效率。
* **营销活动页**：利用简洁的按钮、弹窗组件，配合主题定制，打造风格统一、交互流畅的活动界面。
* **中后台工具平台**：通过灵活的组件扩展与多端适配，满足内部工具多样化的交互与终端访问需求。

无论是初创项目快速验证，还是大型工程长期迭代，StrideUI 都能以简洁、灵活的姿态，助力开发者大步 “Stride” 构建优质界面 。
