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
![Diagram](./images/SQLi-11.jpg)<br>
〇　ユーザ/パスワードを入力します(ユーザ名:test/パスワードtest)<br>

![Diagram](./images/SQLi-12.jpg)<br>

〇　ユーザ名/パスワードに対応するメールアドレスが検索できました！<br>

![Diagram](./images/SQLi-13.jpg)<br>


### SQLインジェクション異常な動作の確認<br>　　  


![Diagram](./images/SQLi-14.jpg)<br>

〇　ユーザ/パスワードを入力します(ユーザ名:test/パスワードtest' OR ' 1=1)<br>

![Diagram](./images/SQLi-15.jpg)<br>

〇　SQLインシェクションによりすべてのメールアドレス一覧が表示されてしまいました。。<br>

![Diagram](./images/SQLi-16.jpg)<br>


##### パケットとログを確認してみましょう！！<br>


[目次に戻る](./README.md) <br>

