---
problem: OnGenerateVisualContent 内でマテリアルプロパティを更新すると InvalidOperationException が発生する
cause: generateVisualContent コールバック実行中に VisualElement のレンダーデータを変更しようとすると禁止されている。このコールバック内で MarkDirtyRepaint() を呼ぶこともこの制約に抵触する。
solution: OnGenerateVisualContent 内では mgc.Allocate() で確保したメッシュへの頂点書き込みのみ行う。マテリアルプロパティの更新や MarkDirtyRepaint() の呼び出しはコールバック外で行う。
environment:
  - Unity 6000.4
  - UI Toolkit
  - UI Shader Graph
limitations:
  - VisualElement のプロパティを変更しない（公式ドキュメント警告）
  - MarkDirtyRepaint() を呼ばない（InvalidOperationException）
related:
  - ui-builder-material.md
  - VisualElement.generateVisualContent
keywords:
  - UI Toolkit
  - generateVisualContent
  - MarkDirtyRepaint
  - InvalidOperationException
  - VisualElement
---
