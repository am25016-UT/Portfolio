# 上原 拓也 – Human Interface / Prototyping ポートフォリオ

工学院大学大学院 工学研究科 機械工学専攻 修士1年  
センシング × AI認識 × ヒューマンインターフェース（非接触UIなど）の**試作開発・プロトタイピング**に関心があります。

---

## プロジェクト一覧（クリックで詳細へ）

| プロジェクト | 概要画像（クリックで詳細へ） |
|---|---|
| [1. AIポーズ認識アプリ（iOS / Swift）](#1-aiポーズ認識アプリios--swift) | [![AI Pose App](images/pose_app.png)](#1-aiポーズ認識アプリios--swift) |
| [2. 非接触UIコンセプト（Gesture + Voice）](#2-非接触uiコンセプトgesture--voice) | [![Non-contact UI](images/noncontact_ui.png)](#2-非接触uiコンセプトgesture--voice) |
| [3. PDMSステンシル製作プロセス開発（修論）](#3-pdmsステンシル製作プロセス開発修論) | [![PDMS](images/pdms.png)](#3-pdmsステンシル製作プロセス開発修論) |
| [4. 自動車部での改善（整備・改善）](#4-自動車部での改善整備改善) | [![Automotive](images/automotive.png)](#4-自動車部での改善整備改善) |
| [5. 3Dプリンタ／ものづくり（試作・治具など）](#5-3dプリンタものづくり試作治具など) | [![3D Printing](images/3d_printing.png)](#5-3dプリンタものづくり試作治具など) |

> ※ 画像は後で差し替えでOKです（例：`images/pose_app.png`）。  
> まずはこのフォーマットをコミットして「見せられる形」を完成させましょう。

---

## 1. AIポーズ認識アプリ（iOS / Swift）

### 概要
スマートフォンのカメラ映像から人体の姿勢情報（特徴点）を取得し、特定のポーズを自動判定するiOSアプリのプロトタイプを開発しました。ダンス練習などにおいて、ユーザーが自身のポーズを簡便に判定できる環境を提供することを目的としています。 :contentReference[oaicite:6]{index=6}

---

### 背景（課題）
既存のダンス支援手段として、アプリ／Webサイト／高度な機器／専門トレーナー／巨大な鏡の使用などがありますが、  
**見本動画を見ながら模倣のみになりがちで、コストや利便性の課題**があると考えました。 :contentReference[oaicite:7]{index=7}

---

### アプローチ（どう解いたか）
iPhoneのカメラ映像から人体の特徴点を取得し、  
**身体各部位の相対位置関係（象限）と関節角度**を用いてポーズを判定する手法を実装しました。 :contentReference[oaicite:8]{index=8}

処理フロー（実装イメージ）
1. iPhoneカメラ映像を取得
2. Vision Frameworkで姿勢推定を実行
3. 身体の特徴点（座標）を取得
4. 頭部を原点とした2次元座標系を設定
5. 特徴点の象限情報＋四肢の角度情報を算出
6. 条件一致時に判定結果を表示 :contentReference[oaicite:9]{index=9}

---

### 使用技術・開発環境
- 開発ツール：Xcode
- 言語：Swift
- 実行端末：iPhone 15
- 姿勢推定：Apple Vision Framework（Human Pose Estimation） :contentReference[oaicite:10]{index=10}

---

### 判定アルゴリズム（判定条件）
ポーズごとに以下を条件として設定しました。
- **12点の特徴点の象限情報**
- **四肢の角度情報（両腕・両足の4点）**
- 角度許容範囲（±5°, ±10°, ±15°） :contentReference[oaicite:11]{index=11}

象限情報と角度情報の両方を満たしたときに、ポーズ成立として判定結果を表示します。 :contentReference[oaicite:12]{index=12}

---

### 評価（成功率）
角度許容範囲を変更し、複数ポーズ・複数被験者で成功率を評価しました。 :contentReference[oaicite:13]{index=13}

| 角度許容範囲 | 平均判定成功率 |
|---|---:|
| ±5°  | 25% |
| ±10° | 59% |
| ±15° | 75% |

※許容範囲を広げるほど成功率が向上することを確認しました。 :contentReference[oaicite:14]{index=14}

---

### 成果（できたこと）
- iOS上で動作するポーズ判定アプリをSwiftで実装
- Vision Frameworkによるリアルタイム姿勢推定（特徴点取得）
- 相対位置（象限）＋角度情報によるポーズ判定ロジックを構築
- 角度許容範囲の違いによる成功率を実験で評価 :contentReference[oaicite:15]{index=15}

---

### デモ
- YouTube：（URLを貼る） :contentReference[oaicite:16]{index=16}

---

### 今後の展望
- 姿勢の向きの判別（首・ひねり動作）
- 上下方向・奥行き方向の判別
- 動的なポーズ判定
- 角度評価の校正化（判定条件プリセットとアプリ統合による誤差低減）
- **条件設定の自動化**（ポーズ数だけ条件を設定する必要があるため） :contentReference[oaicite:17]{index=17}

---

## 2. 非接触UI（ハンドジェスチャー × 音声認識）— 製造現場の作業効率改善提案

### 概要（1〜2行）
ハンドジェスチャーと音声認識を用いて、**手袋を脱着せずに図面・3Dモデル・マニュアル確認を可能にする非接触操作UI**を提案しました。:contentReference[oaicite:0]{index=0}  
製造現場における“中断作業”を減らし、稼働率・生産性・安全性の改善を狙います。:contentReference[oaicite:1]{index=1}

---

### 背景（Why now）
近年、ものづくり工房の新設・拡大や、1人で複数装置を見る現場の増加が進んでいます。:contentReference[oaicite:2]{index=2}  
加えて技能工の高齢化により、製造業の技術者が10年で大きく減少する懸念が示されています。:contentReference[oaicite:3]{index=3}

---

### 顧客（Who）
- 1人で複数の工作機械を取り扱う「ものづくり工房（FabLab）」:contentReference[oaicite:4]{index=4}  
- 企業・大学の試作製作部門:contentReference[oaicite:5]{index=5}  
- 小ロット品を作るものづくり系の中小企業:contentReference[oaicite:6]{index=6}  

---

### 課題（Pain）
複数装置を動かし、都度作るものが違う現場では、図面やマニュアル確認のために**手袋を何度も着脱**し、工程が止まります。:contentReference[oaicite:7]{index=7}  
担い手不足の影響でその頻度は増加傾向であり、教育コストや安全作業のリスクも増えます。:contentReference[oaicite:8]{index=8}

---

### 提案するソリューション（Solution）
安全かつ品質の良い機械加工を行うために、**手袋を脱着せずに図面・3Dモデル・マニュアルをチェック可能な非接触操作UI**を提案します。:contentReference[oaicite:9]{index=9}  
手袋の着脱なくシームレスに確認できることで、高効率な生産と、将来的な人員不足への対応・安全衛生管理にも貢献します。:contentReference[oaicite:10]{index=10}

---

### 技術コンセプト（Technology）
学部時代に開発した**スマホ向け姿勢推定アプリ**のコア技術を、一般のカメラ運用に展開する想定です。:contentReference[oaicite:11]{index=11}  
調査の中でスマホ完結型では特許抵触リスクが高いことが判明したため、**製造現場×コア技術**へ再定義（ピボット）しました。:contentReference[oaicite:12]{index=12}

#### システム構成（案）
Camera
↓
Gesture recognition（手のジェスチャー）
＋ Voice recognition（音声）
↓
図面/3D/マニュアル閲覧UI（非接触操作）

---

### 市場性（概算）
拠点数をベースに、TAM/SAM/SOMを概算しました。:contentReference[oaicite:13]{index=13}  
- TAM：177,832拠点（約1,066億円/年）:contentReference[oaicite:14]{index=14}  
- SAM：43,243拠点（約259.5億円/年）:contentReference[oaicite:15]{index=15}  
- SOM：25,027拠点（約150億円/年）:contentReference[oaicite:16]{index=16}  
※前提：1人あたり月に数時間のロス、月5万円（年60万円）として仮定。今後検証予定。:contentReference[oaicite:17]{index=17}  

---

### 検証結果と課題（Validation）
複数の工作機械を持つ現場での検証により、複数の図面・マニュアル確認で**中断作業が多い**ことが判明しました。:contentReference[oaicite:18]{index=18}  

**課題（事業）**：作業者自身が中断作業を意識していないため、費用を払って解決してもらう販売戦略が重要。:contentReference[oaicite:19]{index=19}  
**課題（技術）**：スマホ→カメラ化に伴う要件定義とUI開発、MVP定義が必要。:contentReference[oaicite:20]{index=20}  

---

### 今後の進め方（マイルストーン案）
- ものづくり企業ヒアリング → MVP要件定義 → PoC検証:contentReference[oaicite:21]{index=21}  
- スマホ→カメラ向けジェスチャー認識技術開発、画面出力ロジック構築、PoC用簡易プロトタイプ作成:contentReference[oaicite:22]{index=22}  
- 将来：建設・医療など別領域探索、海外市場調査、量産向けプロト開発:contentReference[oaicite:23]{index=23}  

---

### 導入効果（想定）
- 電力コスト削減：一括制御・稼働最適により20〜40%削減可能性（月2,000〜4,000円節約の試算）:contentReference[oaicite:24]{index=24}  
- 時間短縮：中断作業（手袋脱着・マニュアル確認・機械切替）の削減、AR UIによりタスク完了時間が21〜24%減少の参考値:contentReference[oaicite:25]{index=25}  
- 運用コスト削減：消耗品・部品摩耗・教育/やり直し工数の削減:contentReference[oaicite:26]{index=26}  

---

### 技術優位性・オリジナリティ
- 姿勢推定アプリの開発経験を活かし、実装可能な開発力を有していること:contentReference[oaicite:27]{index=27}  
- スマホで作成していたプロトタイプを活用でき、スピーディーな開発が可能であること:contentReference[oaicite:28]{index=28}  

---

### デモ
- 動画URL：（後で貼る）

---

## 3. PDMSステンシル製作プロセス開発（修論）

### 概要（1〜2行）
PDMSステンシルの製作プロセスを開発し、再現性・作業性（スループット）の改善を目指しています。

### 背景（課題）
（後で記入）

### 取り組み（どう解いたか）
（後で記入）

### 使用技術
- PDMS
- Microfabrication（微細加工）
- Process Development（工程設計）
- 再現性向上・条件最適化

### 成果（できたこと）
（後で記入）

### 今後
（後で記入）

---

## 4. 自動車部での改善（整備・改善）

### 概要（1〜2行）
自動車部の活動の中で、整備・改善の観察→仮説→実行→検証を回し、改善を行いました。

### 背景（課題）
（後で記入）

### 取り組み（どう解いたか）
（後で記入）

### 使用スキル
- 機械工学の基礎
- 整備・分解・組立
- 既存状態の把握（現状分析）と改善

### 成果（できたこと）
（後で記入）

### 今後
（後で記入）

---

## 5. 3Dプリンタ／ものづくり（試作・治具など）

### 概要（1〜2行）
3Dプリンタを用いた試作・治具制作など、短いサイクルで形にして改善するものづくりを行っています。

### 代表例（箇条書きでOK）
- （後で記入）
- （後で記入）
- （後で記入）

### 使用スキル／ツール
- 3D printing（Bambu Lab）
- CAD / モデリング
- 試作→改善の反復

---

## リンク
- GitHub：このリポジトリ
- 連絡先：（任意）
## Links
- GitHub: This repository
- Contact: (Optional)
