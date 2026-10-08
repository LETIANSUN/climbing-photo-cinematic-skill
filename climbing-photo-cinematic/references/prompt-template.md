# 图像编辑提示词模板

按本图实际情况精简模板，删除不适用段落。花括号内容是待填的创作参数，必须在调用工具前替换。不得把模板中的示例颜色当成用户确认。

## 主编辑

```text
Use case: style-transfer / lighting-weather.
Input 1: EDIT TARGET, {人物、服装、动作和场景的简短描述}.
Input 2, if present: STYLE REFERENCE ONLY. Use its lighting, tonal finish and optical softness; never transfer its person, geometry or route color.
Output one edited version of the target with the original complete {横幅/竖幅及实际宽高比} framing.

CONFIRMED ROUTE: {用户确认的颜色及区域}.
KEEP COLOR on these ORIGINAL route holds only: {手点、脚点、其他本线路岩点的位置/形状}.
DESATURATE: {其他颜色线路；同色但不同线路的明确区域}.
Preserve the route's original hue, chalk, screws, gloss and material. Tone fluorescent colors down tastefully, not into another hue. Do not recolor any non-route hold into the target color. For a black route, keep black surfaces with readable chalk and highlights.
Convert non-route colored holds to {中灰/炭灰，或按用户要求仅明显降饱和}, retaining their exact shapes and positions. Clothing, skin, shoes, plywood structures and wall panels are not included in hold-color desaturation.

SUBJECT LIGHTING: Realistic soft directional {顶光/前侧光，根据原图判断} illuminates the face, shoulders/back, arms/hands, fabric folds and legs. The whole climber should be visibly brighter than the environment with natural skin, soft highlight rolloff and readable black-clothing detail. Do not reshape anatomy or exaggerate muscles.

ENVIRONMENT: Smoothly darken {本图外围/远处的具体区域} while preserving the wall's ORIGINAL {原墙面色相和分区描述}, physical texture, seams and bolt holes. Local brightness may change; wall hue and material stay consistent. Keep deep but readable shadows, no painted black patches.

FOCUS: Keep the ENTIRE climber, fingertips, shoes and active hand/foot holds sharp. Add gradual natural optical softness to {本图前景和外围区域}. Same-plane wall regions should only soften subtly; lighting falloff is the main separation. No radial blur mask, halos or hard cutout boundaries.

{仅有前景人群时添加：Keep every spectator and their original position, silhouette and occlusion. Darken and optically defocus them, reducing white clothing, exposed skin and screen highlights. Do not remove people or invent hidden parts of the climber.}

{仅有垫子/灯带时添加：Retain the foreground mat and lighting fixtures but reduce distracting reflections/glow and softly defocus the foreground.}

{仅已授权去水印时添加：Remove only these overlaid watermarks: 指定位置、文字。Naturally reconstruct covered surfaces. Keep actual clothing/hold brands and physical wall signs.}

INVARIANTS: The exact same person, face/hair, body proportions, original pose, fingers and hand contacts, legs/shoes and original foot contacts, clothing and equipment, all hold geometry/location/count, camera viewpoint and complete crop. Do not invent foothold contacts for suspended feet. Preserve actual text/labels and foreground occlusion. No extra objects, limbs or overlays.
FINISH: Restrained cinematic sports-documentary photography, subtle fine grain, natural skin and material texture. Avoid HDR, heavy orange-teal cast, plastic skin, over-sharpening, overexposed skin, uniform heavy blur, harsh spotlights or opaque black borders.
```

## 一次只修一个局部缺陷

```text
Use case: precise-object-edit.
Edit this finished photograph with ONE LOCAL CORRECTION ONLY.
Target: {位置、相邻参照物、形状；必要时宽高百分比}.
Correction: {例如这个原本黄色的杯状岩点应为中灰，不属于浅绿路线}.
Preserve its geometry, texture, chalk, lighting and exact position.
Keep every other confirmed route hold in its current color. Keep person identity/anatomy/pose/contact points, clothing, wall hue, all scene geometry, current lighting, crowd/occlusion, focus falloff and full framing unchanged. No global regrading or relighting.
```

## 颜色确认与区域示例

| 用户输入 | 执行决策 |
| --- | --- |
| “图1蓝色，图2粉色，你自己优化” | 颜色已确认，分别编辑，无需再问颜色。 |
| “按之前效果处理这张” | 先问本图线路颜色，不继承上一张颜色。 |
| “浅绿线”且左侧有一条明显独立的浅绿线 | 保留范围不明时询问位置；不能默认保留所有绿色。 |
| “中间浅绿线，左侧绿色属于另一条线” | 保留中间，左侧灰化。 |
| “黑线”，两只脚正悬空 | 保持悬空动作；不把附近岩点挪到脚下。 |
| 前景有人遮挡脚部 | 保持遮挡，压暗/虚化；不删除人物或补画隐藏脚部。 |
| 原本黄色岩点被处理成青蓝色 | 该点局部改灰，保留其他已确认的青蓝线路。 |
