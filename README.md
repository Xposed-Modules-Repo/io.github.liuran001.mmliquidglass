# WeChat Liquid Glass

LSPosed module that replaces WeChat's bottom tab bar with a floating liquid-glass
pill, reproducing the look and feel of the KernelSU manager's floating bottom bar.

## Features

- **Live refracting glass** — saturation boost, 4dp blur and rounded-rect SDF
  refraction, sampled from WeChat's own page content every frame. Not a static
  overlay: the list scrolls behind the glass and bends at the rim.
- **Droplet indicator** — pressing fades in a dispersion lens that magnifies the
  tab underneath. Five springs drive its travel, velocity stretch and press scale.
- **Drag to switch** — hold the droplet and drag sideways; it settles on the
  nearest tab when released.
- **Edge to edge** — pages extend under the gesture bar, with the pill floating
  above them; the list can still scroll its last row clear of the pill.
- Follows WeChat's light/dark theme. Unread badges keep their own colour.

## Requirements

- Android 13 (API 33) or newer — the refraction is written in AGSL. Older
  versions fall back to a plain blur.
- WeChat 8.0.77. Other versions are located by layout shape as a fallback, which
  is not guaranteed.
- LSPosed

## Usage

1. Install the APK
2. Enable this module in LSPosed and tick **WeChat** in its scope
3. Force stop WeChat
4. Reopen WeChat

## Notes

- The bar is located by class name first; if a WeChat update renames it, a strict
  structural match is used instead. Should that also miss, WeChat simply keeps
  its own bar — the module never leaves the app without a tab bar.
- A WeChat redesign, or the bar moving to Compose, would need re-adaptation.

## Build

No Gradle or Android Studio:

```bash
./setup-tools.sh   # android.jar / build-tools 34 / libxposed
./build.sh
```

Built against libxposed API 102.

## License

MIT

---

# 微信液态玻璃

一个 LSPosed 模块，把微信的底部标签栏换成悬浮的液态玻璃胶囊，效果对齐
KernelSU 管理器的悬浮底栏。

## 特性

- **实时折射玻璃** —— 饱和度提升、4dp 模糊、圆角矩形 SDF 折射，每帧实时采样
  微信自己的页面内容。不是静态贴图：列表在玻璃后滚动，边缘会随之弯折。
- **液滴指示器** —— 按住时淡入带色散的透镜，把下方的标签放大折射。五条弹簧
  分别驱动位移、速度形变与按压缩放。
- **拖拽切换** —— 按住液滴左右拖动即可切标签，松手落到最近的一个。
- **内容延伸到底** —— 页面铺满到手势条之下，胶囊悬浮其上；列表滚到末尾时
  最后一行仍能完全避开胶囊。
- 跟随微信深色 / 浅色主题，未读红点保持原色。

## 要求

- Android 13（API 33）及以上 —— 折射用 AGSL 实现，更低版本会退回普通模糊。
- 微信 8.0.77。其他版本靠布局结构兜底匹配，不保证可用。
- LSPosed

## 使用方法

1. 安装 APK
2. 在 LSPosed 中启用本模块，作用域勾选**微信**
3. 强制停止微信
4. 重新打开微信

## 说明

- 底栏优先按类名定位；若微信更新改了类名，则改用严格的结构匹配。两者都没
  命中时，微信会保留它自己的原生底栏 —— 本模块不会让应用失去标签栏。
- 微信大改版，或底栏改用 Compose 实现，届时需要重新适配。

## 构建

不需要 Gradle 和 Android Studio：

```bash
./setup-tools.sh   # android.jar / build-tools 34 / libxposed
./build.sh
```

基于 libxposed API 102 构建。

## 协议

MIT
