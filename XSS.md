### [始めに戻る](./README.md/) <br>


# XSSとは？？<br>
<img width="1046" height="683" alt="image" src="https://github.com/user-attachments/assets/d5187e66-dc6c-46b7-a675-bb3e7b096f28" />

【安全なウェブサイトの作り方 - 1.5 クロスサイト・スクリプティング】<br>
 https://www.ipa.go.jp/security/vuln/websecurity/cross-site-scripting.html

## XSSの種類<br>
 ### 反射型XSS
　ユーザが送信するHTTPリクエストパラメータをＨＴＴＰレスポンスとしてHTMLに表示してしまうもの<br>
 ### 格納型XSS
　Webサイトにある掲示板やコメントの機能等を利用して悪意あるスクリプトを実行できるようにするもの<br>
　（反射型のようなパラメータでなく、そのページを閲覧しただけで、任意のスクリプトが実行。。）<br>

 #### 格納型XSSのイメージ<br>
 <img width="1051" height="631" alt="image" src="https://github.com/user-attachments/assets/9f35d9f7-70f0-4b25-9b17-5d5c072ecb56" />


## XSSの体験<br>
以下のような画面遷移で動作するWebアプリケーションを例とします<br>
<img width="1000" height="567" alt="image" src="https://github.com/user-attachments/assets/08e965e6-194e-4d71-a689-f3e189493f97" />


## 【体験要領】

### 事前準備<br>
異常な動作を確認します (その２）で使用する模擬悪性サイトをPythonを使用して起動しておきます<br>

模擬悪性サイトの作成<br>
<img width="1045" height="626" alt="image" src="https://github.com/user-attachments/assets/7d81f6c4-d4b2-4e78-9831-69baabc1a9f3" />
<img width="1037" height="630" alt="image" src="https://github.com/user-attachments/assets/c734e928-6991-4e90-abdd-9badaf9c7d3c" />

Pythonにより起動後、ブラウザでアクセスできることを確認します<br>
<img width="1027" height="615" alt="image" src="https://github.com/user-attachments/assets/afd58d2c-9d40-4cfb-af15-65dad4aaee92" />

### サイトの動作確認<br>

#### 通常の動作を確認します <br>
〇自身のホスト（ブラウザ）からXSS.phpにアクセスします<br>
<img width="1037" height="622" alt="image" src="https://github.com/user-attachments/assets/a95f4b81-3740-4834-b71c-c185a6728d34" />

〇入力フォームに名前/URLを入力します<br>
<img width="1031" height="631" alt="image" src="https://github.com/user-attachments/assets/42e17981-8e8d-4d55-8890-73f9c24ae7a0" />

 ここでは　名前:gorosuke  "URL：http://www.yahoo.co.jp" と入力しています　<br>
〇入力した情報を確認し登録を実施します<br>
<img width="1035" height="638" alt="image" src="https://github.com/user-attachments/assets/4aca47b2-66e3-4706-8ecd-1065e6bfb30f" />

〇登録された旨が表示されます<br>
<img width="1033" height="596" alt="image" src="https://github.com/user-attachments/assets/8bf5d05b-47e5-46b7-9346-f62fa623b489" />

#### 異常な動作を確認します（その１）<br>
〇自身のホスト（ブラウザ）からXSS.phpにアクセスします<br>
<img width="1037" height="622" alt="image" src="https://github.com/user-attachments/assets/a95f4b81-3740-4834-b71c-c185a6728d34" />

〇スクリプトが実行可能かを確認します<br>
<img width="1028" height="591" alt="image" src="https://github.com/user-attachments/assets/3dbfa608-2058-40cf-a328-f8fa73563a22" />
　　⇒　図のようにJavaScriptが実行されることが確認できます<br>

〇”Cookie情報を表示するスクリプト”を入力し、実行します<br>
<img width="1037" height="593" alt="image" src="https://github.com/user-attachments/assets/64af677c-e16b-4ab8-bf5c-aabe316d11f8" />

<img width="1038" height="595" alt="image" src="https://github.com/user-attachments/assets/6905dd4d-80fa-4dc9-8f83-b4ac80c24002" />
   ⇒　図のように自身のCookie情報を取得することができます・・<br>

#### 異常な動作を確認します (その２）<br>

今回のイメージ：　”模擬悪性サイトにCookie情報を転送するスクリプト”を入力し、実行します<br>
                  ⇒　これにより外部にサイトに自身のCookie情報が漏えいしてしまうことになります。。<br>
<img width="1040" height="603" alt="image" src="https://github.com/user-attachments/assets/69fc8c89-c7c0-4ab6-9ae8-124522c8c456" />

〇自身のホスト（ブラウザ）からXSS.phpにアクセスします<br>
<img width="1056" height="602" alt="image" src="https://github.com/user-attachments/assets/84af90d5-661b-4190-b91f-caff82bde454" />

〇”模擬悪性サイトにCookie情報情報を転送するスクリプト”を入力し、実行します<br>
<img width="1047" height="608" alt="image" src="https://github.com/user-attachments/assets/2ce37946-3ba4-474a-a2a3-98f15c2e87e7" />

上記のスクリプトを埋め込んたHTMLファイルを作成すると。。<br>
<img width="997" height="593" alt="image" src="https://github.com/user-attachments/assets/3672ac23-f24c-4114-b2fb-591e64faca0b" />
<img width="1026" height="557" alt="image" src="https://github.com/user-attachments/assets/0e995c66-670c-405f-84f1-2069ee1e4d69" />

同じように悪性模擬サイトにCookie情報が転送されてしまうことになります。。。<br>
<img width="1032" height="527" alt="image" src="https://github.com/user-attachments/assets/17524d6e-214a-486a-a585-ab4401b11b61" />


### パケットとログを確認してみましょう！！<br>
今回XSS攻撃を受けた内容についてサーバーのログ及びパケットで確認してみます！！<br>
<img width="1042" height="632" alt="image" src="https://github.com/user-attachments/assets/da4483c6-af46-4c0d-9358-28fd88b54d9b" />

〇　サーバーのアクセスログについて<br>
今回の環境におけるWebサーバーのアクセスログは以下の場所になります<br>
more /var/log/apache2/access_log<br>
<img width="1022" height="572" alt="image" src="https://github.com/user-attachments/assets/218fe320-3f52-4e7e-b91b-acce98a061af" />

〇　サーバーのパケット取得について<br>
 サーバー上でTcpdumpを起動し、該当するパケットを取得します<br>






cyber chefを使用してパケットとログをデコードします！<br>
https://gchq.github.io/CyberChef/<br>

#### [おさらい]エンコードとは？？<br>

![Diagram](./images/xss-27.jpg)<br>
![Diagram](./images/xss-28.jpg)<br>
![Diagram](./images/xss-29.jpg)<br>

cyber chefを使用してURLエンコードされた場所をデコードします！<br>
![Diagram](./images/xss-23.jpg)<br>

![Diagram](./images/xss-24.jpg)<br>

![Diagram](./images/xss-25.jpg)<br>

![Diagram](./images/xss-26.jpg)<br>


![Diagram](./images/xss-30.jpg)<br>

[目次に戻る](./README.md) <br>

