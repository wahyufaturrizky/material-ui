---
title: React Tabs（选项卡）组件
components: Tabs, Tab, TabScrollButton, TabContext, TabList, TabPanel
githubLabel: 'component: Tabs'
materialDesign: https://material.io/components/tabs
waiAria: 'https://www.w3.org/TR/wai-aria-practices/#tabpanel'
---

# Tabs 选项卡

<p class="description">使用选项卡，你可以轻松地浏览和切换不同的视图。</p>

对于在同一层次，并且息息相关的内容组，使用选项卡能够将它们分组并且在其之间切换。

{{"component": "modules/components/ComponentLinkHeader.js"}}

## 基础选项卡

A basic example with no frills.

{{"demo": "pages/components/tabs/BasicTabs.js", "bg": true}}

### 包装的标签

对于那些比较长的标签，它们会被自动包装成选项卡。 如果标签超出了选项卡的长度，它则会溢出，并且文本会隐藏。

{{"demo": "pages/components/tabs/TabsWrappedLabel.js", "bg": true}}

### 禁用选项卡

选项卡的 `disabled` 属性能将其设置为禁用状态。

{{"demo": "pages/components/tabs/DisabledTabs.js", "bg": true}}

## 固定的选项卡

固定的选项卡应与定量的选项卡一起使用，而将它们整齐放置则会有助于用户的肌肉记忆。

### 全宽

若是较小的视图，则应使用 `variant="fullWidth"` 属性。 在这个演示中你还可以借鉴用 [react-swipeable-views](https://github.com/oliviertassinari/react-swipeable-views) 来设置选项卡的过渡动画，并且在使用触摸设备时滑动标签。

{{"demo": "pages/components/tabs/FullWidthTabs.js", "bg": true}}

### 居中对齐

而对于较大的视图，则应使用 `centered` 此属性。

{{"demo": "pages/components/tabs/CenteredTabs.js", "bg": true}}

## 可滚动的选项卡

### 自动显示滚动按钮

左右滚动按钮将自动在桌面显示，并在移动设备上隐藏。 （基于视图宽度）

{{"demo": "pages/components/tabs/ScrollableTabsButtonAuto.js", "bg": true}}

### 强制显示滚动按钮

通过使用 `scrollButtons={true}` `allowScrollButtonsMobile` 属性，无论当前视图宽度如何，都会显示左右的滚动按钮（保留空间）

{{"demo": "pages/components/tabs/ScrollableTabsButtonForce.js", "bg": true}}

如果你想确保按钮始终可见，那么你应该自定义不透明度：

```css
.MuiTabs-scrollButtons.Mui-disabled {
  opacity: 0.3;
}
```

{{"demo": "pages/components/tabs/ScrollableTabsButtonVisible.js", "bg": true}}

### 永久隐藏滚动按钮

你可以使用 `scrollButtons={false}` 属性来永远隐藏左右的滚动按钮。 所有的滚动比如通过用户代理的滚动机制来发起（例如，左右滑动，移动鼠标滑轮等等）。

{{"demo": "pages/components/tabs/ScrollableTabsButtonPrevent.js", "bg": true}}

## 自定义的选项卡

以下是自定义组件的一个示例。 您可以在[重写文档页](/customization/components/)中了解有关此内容的更多信息。

{{"demo": "pages/components/tabs/CustomizedTabs.js", "bg": true}}

🎨 如果您还在寻找灵感，您可以看看 [MUI Treasury 特别定制的一些例子](https://mui-treasury.com/styles/tabs/)。

## 垂直的选项卡

使用 `orientation="vertical"` 来使垂直标签代替默认的水平标签。

{{"demo": "pages/components/tabs/VerticalTabs.js", "bg": true}}

请注意，你可以使用 `visibleScrollbar` 来恢复显示滚动条。

## 导航选项卡

默认情况下，选项卡会使用 `按钮` 组件，但您也可以提供自定义的标签或组件。 下面是一个实现导航选项卡的例子：

{{"demo": "pages/components/tabs/NavTabs.js", "bg": true}}

## 图标选项卡

选项卡的标签可以是所有的图标或者所有的文本。

{{"demo": "pages/components/tabs/IconTabs.js", "bg": true}}

{{"demo": "pages/components/tabs/IconLabelTabs.js", "bg": true}}

## 无障碍设计

(WAI-ARIA: https://www.w3.org/TR/wai-aria-practices/#tabpanel)

您需要采取以下步骤，来为无障碍技术提供一些必要的信息：

1. 在 `Tabs` 上应用 `aria-label` 或 `aria-labelledby` 标签。
2. 通过设置 `id`、`aria-controls` 和 `aria-labelledby` ，`Tab` 需要连接到其对应的 `[role="tabpanel"]`。

实现这样的设计例子可以在本页面的演示中找到。 我们还在 `@material-ui/lab` 中发布了不需要额外工作就能使用的 [一个实验性的 API](#experimental-api)。

### 键盘导航

该组件使用“手动激活”的行为来实现键盘导航。 如果你想切换到“选择自动跟随焦点”（selection automatically follows focus）的行为，你必须将 `selectionFollowsFocus` 传递给 `Tabs` 组件。 WAI-ARIA 项目实践中对 [如何决定什么时候选择自动跟随焦点](https://www.w3.org/TR/wai-aria-practices/#kbd_selection_follows_focus) 进行了详细的指导。

#### 演示

下面的两个演示只是在键盘导航行为上有所区别。 聚焦到其中一个选项卡，然后用方向键导航你就可以注意到其中的差异。

```jsx
/* 那个跟随焦点的选项卡 */
<Tabs selectionFollowsFocus />
/* 需要手动选择选项卡中的每一个选项 */
<Tabs />
```

{{"demo": "pages/components/tabs/AccessibleTabs.js", "bg": true}}

## 实验性的 API

遵循 [WAI-ARIA 项目实践](https://www.w3.org/TR/wai-aria-practices/#tabpanel)，`@material-ui/lab` 提供了工具集组件，该组件通过注入属性的方式来实现无障碍设计的选项卡。

{{"demo": "pages/components/tabs/LabTabs.js", "bg": true}}
