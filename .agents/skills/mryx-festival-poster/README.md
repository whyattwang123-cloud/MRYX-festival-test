# mryx-festival-poster v2

这是升级版的 `mryx-festival-poster` Skill。

## 这次升级了什么
相比第一版，这一版核心增加了：

1. **固定 logo 素材逻辑**
2. **固定产品 packshot 素材逻辑**
3. **背景生成 + 后期合成** 的两段式思路
4. 输出中新增：
   - Selected Assets
   - Background Prompt
   - Compositing Instructions

## 推荐目录结构
将本目录放到：

```text
.agents/skills/mryx-festival-poster/
```

并将你真实的素材放到：

```text
assets/logos/
assets/products/
```

然后维护：

```text
assets/brand-guides/asset-manifest.md
```

## 推荐使用方式
### 方式一：先做背景
示例：

```text
使用 mryx-festival-poster skill。
节气：立春
风格：清新、温暖、高级
尺寸：9:16
指定 logo：assets/logos/mryx-logo-main.png
指定产品：assets/products/fish-oil-giftbox.png
请输出：Selected Assets、Poster Direction、Background Prompt、Compositing Instructions。
先不要生成最终带产品海报，只生成背景方案。
```

### 方式二：后续再做合成
等 Codex 出图稳定后，你可以让它：
- 先根据 Background Prompt 生成背景
- 再把固定 logo / 产品 PNG 合成进去

## 你下一步该做什么
1. 把真实 logo PNG 放进 `assets/logos/`
2. 把真实产品 PNG 放进 `assets/products/`
3. 把 `asset-manifest.md` 里的占位文件名改成你的真实文件名
4. 用一个简单需求测试输出结构

## 临时注意
在 Codex Web 图片预览完全稳定前，建议先把这个 Skill 作为：
- 设计规则生成器
- 背景 Prompt 生成器
- 合成说明生成器

等预览问题恢复后，再继续测试“自动生成背景 + 合成真实素材”。
