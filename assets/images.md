# Demo 图片清单

Demo 页面 `index.html` 共引用 5 张图片，全部通过 `images.unsplash.com` CDN 热链接，仓库内不保存副本。

所有图片均遵循 [Unsplash License](https://unsplash.com/license)。

## 清单

| # | 用于 | 题材 | URL |
|---|---|---|---|
| 1 | 01 Onboarding 全屏 hero | 晨雾松林 | `https://images.unsplash.com/photo-1470071459604-3b5ec3a7fe05` |
| 2 | 02 Home 列表第 1 条 | 山毛榉林光斑 | `https://images.unsplash.com/photo-1441974231531-c6227db76b6e` |
| 3 | 02 Home 列表第 2 条 | 金山湖 | `https://images.unsplash.com/photo-1501785888041-af3ef285b470` |
| 4 | 02 Home 列表第 3 条 | 落日山脉 | `https://images.unsplash.com/photo-1469474968028-56623f02e42e` |
| 5 | 03 Event 头图 | 星空山脊 | `https://images.unsplash.com/photo-1519681393784-d120267933ba` |

URL 参数约定：

```
?auto=format&fit=crop&w=<宽度>&q=<质量>
```

- hero 大图 `w=800`，列表缩略图 `w=400`
- 全部采用 `fit=crop` 保证比例一致
- 每张 `<img>` 都带 `onerror` 兜底，加载失败时降级为渐变占位底色

## 换成你自己的图

替换时保持这三点，版面不会散：

1. **hero 图纵横比接近 3:4，主体偏上**（顶部有状态栏和悬浮按钮）
2. **缩略图用正方形，视觉重心居中**（容器是 78×78 圆角裁剪）
3. **五张图的调性一致** —— 同为冷调晨光或同为暖调黄昏，混搭会让界面显得廉价

## 使用前请确认

- [ ] 图片中没有可识别的人物面部（涉及肖像权）
- [ ] 图片中没有清晰的商标或品牌标识
- [ ] 不准备把图片原样打包转售
- [ ] 保存了每张图的 Unsplash 详情页链接与下载时间
- [ ] 项目进入生产环境前，评估是否替换为商业图库素材

详细的版权边界见仓库根目录 [`NOTICE.md`](../NOTICE.md)。
