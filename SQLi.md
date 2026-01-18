### [始めに戻る](./README.md/) <br>

# SQLインジェクションとは？？<br>
<img width="1043" height="678" alt="image" src="https://github.com/user-attachments/assets/671e48b5-7254-46a4-b072-0464b5d49a20" />
<img width="1042" height="680" alt="image" src="https://github.com/user-attachments/assets/09227823-fb58-41bc-8547-f988689e2da5" />


参考資料：【安全なウェブサイトの作り方 - SQLインジェクション】<br> 
https://www.ipa.go.jp/security/vuln/websecurity/sql.html<br>

## 【SQLインジェクションの体験】

### サイト構成<br>
以下のようなサイト構成を例として実習します<br>
<img width="1042" height="635" alt="image" src="https://github.com/user-attachments/assets/727adb4c-06b4-4fc7-9293-180fcd1b9c44" />


#### 体験前の事前事前準備<br>
##### データベースの作成<br>

PaizaCloud上にあるDBサーバー（MYSQL）にログインし、以下の作業を実施<br>
PaizaCloudのWeb画面に左側にあるコンソールを起動<br>
sudo su でrootになっておく<br>

<img width="1041" height="643" alt="image" src="https://github.com/user-attachments/assets/c490b55b-853a-412c-8136-ddf05ce69c82" />
<img width="1026" height="632" alt="image" src="https://github.com/user-attachments/assets/8240080b-e5c6-481f-8253-e0b2eb7a0f2b" />

##### 作成したデータベースの確認<br>
<img width="1018" height="624" alt="image" src="https://github.com/user-attachments/assets/c2aab621-52e4-4a2b-9d81-244b9b6bd268" />


##### ログアウトして、再度rootでログイン後、作成ユーザに権限を持たせる<br>
<img width="1041" height="623" alt="image" src="https://github.com/user-attachments/assets/bbef9cc0-868a-4a7c-ac0a-292d785f09af" />
<img width="1020" height="632" alt="image" src="https://github.com/user-attachments/assets/14f4a222-c6e7-4df8-bd70-d79eb94b5b86" />


##### 再度作成ユーザ(gorosuke5656)でログイン<br>
<img width="1032" height="634" alt="image" src="https://github.com/user-attachments/assets/eca3038b-0bac-4968-81bc-eafabee2f5ca" />
<img width="1009" height="634" alt="image" src="https://github.com/user-attachments/assets/70291104-557d-4183-b648-92cc18c3c36c" />

##### ユーザID、パスワード、メールアドレスをDBに登録し、登録状態を確認します
<img width="1033" height="635" alt="image" src="https://github.com/user-attachments/assets/ede6ec92-2dc7-40ed-b37d-68d90ac8420c" />
<img width="1012" height="616" alt="image" src="https://github.com/user-attachments/assets/799f4b3b-f151-462d-a6cb-4e2e629e1619" />

##### 実習用HTMLファイル及びPHPスクリプトをアップロード<br>
<img width="1042" height="633" alt="image" src="https://github.com/user-attachments/assets/9c142152-60b8-4761-b817-8e47f88f8cc4" />
<img width="1036" height="629" alt="image" src="https://github.com/user-attachments/assets/19e654ed-7e6b-4c9a-a57f-8240fdfadbfd" />


### SQLインジェクション体験：正常な動作の確認<br>
<img width="1039" height="632" alt="image" src="https://github.com/user-attachments/assets/1ac3f49d-9428-4fb3-b365-0b45a6069642" />

#### ユーザ/パスワードを入力します(ユーザ名:test/パスワードtest)<br>
<img width="1033" height="630" alt="image" src="https://github.com/user-attachments/assets/82d515ff-0b34-46c5-9b55-f339ddf35f8e" />

#### ユーザ名/パスワードに対応するメールアドレスが検索できました！<br>
<img width="1037" height="628" alt="image" src="https://github.com/user-attachments/assets/f63b73f1-f0e2-4dc4-ba26-95b6b7548f60" />



### SQLインジェクション異常な動作の確認<br>　　  
<img width="1041" height="634" alt="image" src="https://github.com/user-attachments/assets/a12259b5-1f5a-43a8-b61a-e1b86b363bf6" />

#### ユーザ/パスワードを入力します(ユーザ名:test/パスワードtest' OR ' 1=1)<br>
<img width="1016" height="615" alt="image" src="https://github.com/user-attachments/assets/4e230d0d-0bfc-406b-82f1-3208d1b09fbc" />

#### SQLインシェクションによりすべてのメールアドレス一覧が表示されてしまいました。。<br>
<img width="1046" height="635" alt="image" src="https://github.com/user-attachments/assets/cebd6b9a-e5bd-4992-99ed-0ab7ffd10214" />


#### パケットとログを確認してみましょう！！<br>

##### パケットの取得及び確認<br>
<img width="1039" height="637" alt="image" src="https://github.com/user-attachments/assets/d258d3b6-39cb-48fa-8a91-a9b2650ce76d" />

<img width="1030" height="617" alt="image" src="https://github.com/user-attachments/assets/926b0436-f43a-4e35-bd51-0db51d0027d5" />

<img width="1037" height="630" alt="image" src="https://github.com/user-attachments/assets/7c08bbfb-e976-4576-a82c-02fb65b79f05" />

<img width="1037" height="635" alt="image" src="https://github.com/user-attachments/assets/95403566-7b41-4f2a-88bb-0468c7d4aeb6" />

##### 取得パケットからWiresharkによるオブジェクトのエクスポート<br>
<img width="1040" height="631" alt="image" src="https://github.com/user-attachments/assets/9205b725-a4c6-430c-912d-20905abe18ba" />

<img width="1039" height="619" alt="image" src="https://github.com/user-attachments/assets/9bc74397-5cb3-420a-9d21-b848dc6916fb" />

##### Cyberchefによる文字列の確認<br>
<img width="1031" height="563" alt="image" src="https://github.com/user-attachments/assets/18bc4be4-0a36-43de-8039-0c48960de273" />

##### アクセスログの取得及び確認<br>
<img width="1033" height="625" alt="image" src="https://github.com/user-attachments/assets/b5d65221-bae5-4f15-91c0-28a948064c91" />

##### 【おさらい】GET送信とPOST送信の違い<br>
<img width="1029" height="659" alt="image" src="https://github.com/user-attachments/assets/8585fcda-d64e-40e7-b09a-5680b2fd8275" />

##### 上記の通り通常POST送信されたログはWebのアクセスログに残らないため、MYSQLでクエリ－ログを取得できるように設定します<br>

###### MYSQLクエリログ取得のための設定<br>
<img width="1036" height="613" alt="image" src="https://github.com/user-attachments/assets/a4f11fe7-7805-49b2-a536-6dd610001183" />
###### 設定したクエリログの確認<br>
<img width="1021" height="615" alt="image" src="https://github.com/user-attachments/assets/71462280-2198-4322-a54c-9cb0e1dfa074" />

<img width="1026" height="665" alt="image" src="https://github.com/user-attachments/assets/7b441395-e53b-4506-85e2-bee918efce5c" />

これによりPOST送信された内容を確認することができます!!<br>



[目次に戻る](./README.md) <br>

