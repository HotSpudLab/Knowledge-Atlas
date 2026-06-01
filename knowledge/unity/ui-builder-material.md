---
problem: UI Builder でカスタム VisualElement のマテリアルプロパティを変更しても Preview に反映されない
cause: UI Builder 環境では `style.unityMaterial` は Null のまま。マテリアルは UXML やテンプレートから設定されるため、`style`（インラインスタイルのみを反映）には入らず、`resolvedStyle`（UXML・USS・インラインの全スタイルソースから解決した値）にしか存在しない。
solution: マテリアルを取得する際は `style.unityMaterial` ではなく `resolvedStyle.unityMaterial` をフォールバックとして確認する。取得したマテリアルに対して `Material.SetXxx()` でプロパティを設定する。
environment:
  - Unity 6000.4
  - UI Toolkit
  - UI Shader Graph
limitations:
  - `resolvedStyle` は読み取り専用。書き込みには `style` を使用する必要がある。
  - `style.unityMaterial` は UI Builder 環境ではほとんど空っぽになる。
related:
  - generate-visual-content.md
  - IStyle.unityMaterial
  - IResolvedStyle.unityMaterial
keywords:
  - UI Toolkit
  - UI Builder
  - resolvedStyle
  - unityMaterial
  - style
  - Material
  - UXML
---
