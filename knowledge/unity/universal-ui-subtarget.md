---
problem: UI Shader Graph で Vertex Color ノードを使用するとシェーダコンパイルエラーが発生する
cause: UI Toolkit の UniversalUISubTarget の頂点構造体は、標準の VertexColor セマンティクスを持たない。
solution: Vertex Color を使わず、マテリアルプロパティまたは他の方法で色データを渡す。
environment:
  - Unity 6000.4
  - UI Toolkit
  - UI Shader Graph
  - Universal Render Pipeline
limitations:
  - UniversalUISubTarget では頂点カラーによるデータ受け渡しが不可能。
related:
  - ui-builder-material.md
keywords:
  - UI Toolkit
  - UniversalUISubTarget
  - Vertex Color
  - Shader Graph
  - Shader Error
---
