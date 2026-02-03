# MagickSimpleConvert

当アプリは、ImageMagickのフロントエンドです。

---
## このアプリについて
本アプリは **Microsoft Copilot によって作成された Copilot 製アプリ**です。  
Windows 11 + PowerShell 7.5.4 で動作確認済みですが、5.1でも動作します。

![MagickSimpleConvert](https://github.com/user-attachments/assets/c55025d6-340f-42d9-ac1e-8be44c08e482 "アプリウィンドウ")
---
## 本アプリはPowerShell と WPFで動作します、別途ランタイム等のインストールは必要ありません。
ImageMagickをインストールし、コマンドから使用できるようにしてください。  
ImageMagickのmagick.exeと同じフォルダに配置しても動作します。

ImageMagick を内部で利用し、  
「必要なことだけを確実に行う」という思想で構築されています。

- JPG → JPG/PNG  
- PNG → JPG/JPG  
- SVG / PDF → JPG/PNG（高品質レンダリング対応）  

といった最小限かつ実用的な変換を高速に実行します。

---

## ✨ 特徴

### ✔ シンプルで迷わない  
変換対象は JPG / PNG のみに限定。  
余計な機能を排除し、軽量で扱いやすい構成です。

### ✔ SVG / PDF の高品質レンダリング  
- 入力側に `-density` を適用  
- 出力側に透明処理（必要な場合のみ）  
- ImageMagick の挙動に合わせた最適化済み

### ✔ 透明背景の扱いに最適化  
- SVG → PNG の透明処理  
- PDF → PNG は透明を強制しない  
- ラスター画像は元の透明情報に従う

### ✔ バッチ処理対応  
複数ファイルをまとめて変換できます。

---

## 📦 必要環境

- Windows  
- PowerShell 5 以上  
- ImageMagick（`magick.exe` がパスに通っていること）

---

## 🚀 使い方

### 1. 通常の実行方法
1. `画像変換.ps1` を実行  
2. 変換したいファイルをウィンドウにドラッグ＆ドロップ  
3. 指定した出力フォルダに変換結果が生成されます

---

### 2. ショートカットから実行する方法（推奨）

MagickSimpleConvert をより簡単に起動したい場合は、  
PowerShell を非表示で起動するショートカットを作成できます。

1. デスクトップを右クリック → **新規作成 → ショートカット**
2. 「項目の場所」に以下を入力
```
pwsh.exe  -WindowStyle Hidden -ExecutionPolicy Bypass -File .\画像変換.ps1
```
3. 作成したショートカットを、`画像変換.ps1` と同じフォルダに置く  
4. ショートカットをダブルクリックすると、アプリが起動します

PowerShell ウィンドウを表示せずに起動できるため、  
通常のアプリのように扱うことができます。

---

## ⚙ 実装のポイント

### 入力側オプション  
- SVG / PDF の場合のみ `-density` を付与  
- 入力ファイルは常にこの後に追加

### 出力側オプション  
- PNG の場合のみ透明処理（`-background none` / `-alpha on`）  
- PDF → PNG の場合は透明を強制しない  
- JPG の場合は `-quality` のみ

### 実際のコマンド例（ログ出力）
```
magick -density 300 "input.svg" -background none -alpha on -quality 75 "output.png"
```

---

## 📁 ライセンス

このプロジェクトは自由に利用・改変できます。  
ImageMagick のライセンスに従ってください。

---

## 📝 制作


**Microsoft Copilot**  

