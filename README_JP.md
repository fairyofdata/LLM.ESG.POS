**🌐 Available Versions:**  [🇰🇷 英語(English)](/README.md) | [🇯🇵 한국어(Korean)](/README_KR.md)  

---

# LLMベースのESG重視ポートフォリオ最適化サービス 📊🌱

> 🏆🥈第8回産学連携ソフトウェアプロジェクト発表展示会優秀賞(2位)受賞</br>
> 🏆🥈2024光云大学人工知能融合大学卒業展示会優秀賞(2位)受賞

このリポジトリは、**LLMベースのESG重視ポートフォリオ最適化サービス**プロジェクトに関するものです。ESG（環境、社会、ガバナンス）基準と高度なポートフォリオ最適化技術を統合することで、ユーザーにパーソナライズされたESG重視の投資ポートフォリオを提供します。大規模言語モデル（LLM）を活用してテキストデータを処理・評価することで、投資家は企業のESGスコアを分析し、自身の好みに基づいて最適化されたポートフォリオを生成できます。

---

## UI/UX中心のプロジェクト紹介  
**UI/UX紹介動画をご覧になりたい方は、以下の![YouTube](https://img.shields.io/badge/YouTube-%23FF0000.svg?style=for-the-badge&logo=YouTube&logoColor=white)サムネイルをクリックしてください。**  

(*このタブを保持したい場合は、サムネイルを右クリックし、**「新しいタブでリンクを開く」**を選択してください。*)  

[![動画タイトル](https://img.youtube.com/vi/kHAtgLC4PJY/0.jpg)](https://www.youtube.com/watch?v=kHAtgLC4PJY)  

---

## 目次  
1. [プロジェクト概要](#プロジェクト概要)  
2. [主な機能](#主な機能)  
3. [インストール方法](#インストール方法)  
4. [使用方法](#使用方法)  
5. [プロジェクト構造](#プロジェクト構造)  
6. [今後の拡張可能性](#今後の拡張可能性)  
7. [ライセンス](#ライセンス)  

---

## プロジェクト概要  
近年、ESGは企業の長期的な持続可能性と安定性を評価するための重要な指標となっています。しかし、従来のESG評価手法は、非専門的な投資家にとって透明性やアクセス性に欠けることがよくあります。本プロジェクトでは、LLMを活用したテキストベースの評価とBlack-Littermanモデルを適用したポートフォリオ最適化により、これらの課題に取り組みます。これにより、ESG要素と財務収益をバランスよく調整したカスタマイズポートフォリオを提供します。

### 主な目標  
1. **技術実装**: ESG評価のためのLLMベースのパイプラインを開発し、最適化されたポートフォリオを生成。  
2. **ユーザー中心のサービス**: ユーザー定義の基準と好みに基づくカスタマイズポートフォリオを提供。  

---

## 主な機能  
1. **テキストデータ収集と処理**  
   - `Selenium`と`BeautifulSoup`を使用して、選択した企業に関連する記事を複数のソースから収集。  
   - データを`MongoDB`に保存して効率的に管理。  
   - 収集されたデータを前処理し、企業名を匿名化し、無関係な内容をフィルタリング。  

2. **LLMベースのESGスコア算出**  
   - OpenAI APIを使用して収集した記事のESG関連性を評価し、ESG要素と感情に基づいてラベリング。  
   - 独立したESG評価を可能にするために、`KoElectra`モデルを微調整してAPI依存度を削減。  

3. **包括的なESG評価**  
   - 環境、社会、ガバナンス要素の重みをユーザーが調整し、カスタマイズされた評価を提供。  
   - 財務中心、ESG中心、バランス中心の投資スタイルに基づいてスコアを動的に調整。  
   - 複数のESG評価機関の基準を統合したスコアモデルを使用して、大手機関の評価範囲外の企業も評価可能。  

4. **Black-Littermanモデルを活用したポートフォリオ最適化**  
   - Yahoo Financeデータを使用して選択された企業の市場データと共分散行列を計算。  
   - ユーザーのESG調整スコアをBlack-Littermanモデルに統合し、ユーザーの好みに基づいた期待収益を計算。  
   - `cvxopt`を使用して、最大資産比率などの制約条件を考慮した最適化ポートフォリオ比率を計算。  

5. **Streamlitベースのユーザーインターフェース**  
   - ユーザーフレンドリーなインターフェースを通じてESGの好みを入力し、最適化されたポートフォリオを視覚化。  
   - ESGの重みや投資スタイルを調整できるインタラクティブなスライダーを提供。  
   - 予想収益、ボラティリティ、シャープレシオなどのポートフォリオ指標を視覚化。  

---

## インストール方法  
1. **リポジトリをクローン**  
   ```bash  
   git clone https://github.com/fairyofdata/LLM-ESG-POS.git  
   cd LLM-ESG-POS  
   ```  

2. **必要なパッケージをインストール**  
   ```bash  
   pip install -r requirements.txt  
   ```  

3. **Streamlitアプリを実行**  
   ```bash  
   streamlit run app.py  
   ```  

---

## 使用方法  
1. **データ収集**: 企業ティッカーとデータソースを設定して記事を収集。  
2. **ESGの好みを設定**: Streamlit UIを使用して環境、社会、ガバナンス要素の重みを設定。  
3. **投資スタイルを選択**: 財務中心、ESG中心、バランス中心のポートフォリオオプションから選択。  
4. **ポートフォリオ結果を確認**: ポートフォリオ構成や予想収益、ボラティリティなどのパフォーマンス指標を確認。  

---

## プロジェクト構造  
![Architecture](https://github.com/fairyofdata/LLM.ESG.POS/blob/master/%EC%8B%9C%EC%8A%A4%ED%85%9C%20%EA%B5%AC%EC%84%B1%EB%8F%84.drawio.png)  

```plaintext  
├── data/                   # データおよびESGスコアテーブル  
├── src/                    # ESGスコア算出およびポートフォリオ最適化のソースコード  
│   ├── data_processing.py   # LLMベースのテキスト処理  
│   ├── esg_scoring.py       # ESGスコア算出関数  
│   ├── portfolio_optimization.py  # Black-Littermanを使用した最適化  
│   └── ui/                  # Streamlit UIコード  
├── app.py                  # メインアプリケーションスクリプト  
├── README.md               # プロジェクトドキュメント  
└── requirements.txt        # 依存パッケージ一覧  
```  

---

## 今後の拡張可能性  
1. **ESG評価の拡張**: 追加のESG評価ソースを統合し、リアルタイムニュースアップデートを反映。  
2. **非上場企業への対応**: LLMを活用してスタートアップや非公開企業の評価メカニズムを開発。  
3. **最適化の制約条件改善**: ポートフォリオの多様化を促進するため、セクターごとの制約条件を追加。  

---

## プロジェクト概要  
**KWU第8回産学協力SWプロジェクト & AI融合卒業プロジェクト**  
- **指導教員**: チョ・ミンス教授（光云大學校 情報融合学科）  
- **協力企業**: ビリオンズラボ（ヒョ・スジン博士）  
- **貢献チーム**: Team KWargs（ペク・ジホン（PM）、キム・ナヨン、チャン・ハンジェ）  

---

## ライセンス  
本プロジェクトはMITライセンスに基づいています。詳細は[LICENSE](LICENSE)ファイルをご覧ください。  