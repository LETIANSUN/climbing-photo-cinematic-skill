# 攀岩照片电影感

让攀爬者与目标线路更突出。

![黑线攀岩照片处理前后对比](docs/images/black-route-before-after.jpg)

**左：原图 · 右：处理后**

- 保留目标线路颜色，减弱其他岩点的色彩干扰。
- 加强人物受光，压暗并适度虚化外围环境。
- 保持墙壁原有色调，尽量保留原动作与场景细节。

## 使用

上传照片后，在 Codex 中输入：

```text
使用 $climbing-photo-cinematic 优化这些照片：
第一张蓝线，第二张粉线。突出人物，保留墙壁色调。
```

未说明线路颜色时，会先询问确认；同色岩点属于不同线路时，确认保留区域。也可以提供风格参考图。

## 安装

通过 `$skill-installer` 安装本仓库的 `climbing-photo-cinematic` 子目录，或将整个技能文件夹复制到 Codex 的用户技能目录。需要支持内置图像编辑的 Codex。

[技能说明](climbing-photo-cinematic/SKILL.md) · [提示词模板](climbing-photo-cinematic/references/prompt-template.md) · [GitHub 上传教程](docs/github-upload.md)
