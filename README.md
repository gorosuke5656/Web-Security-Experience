# Web-securityの脆弱性及び対策体験【脆弱性体験及びパケット、ログ調査編】<br>

〇　Paiza cloudを使用したWebセキュリティ体験の資料及びコードです<br>

１ Paiza cloudとは？？::::[次のチャプターへ進む](./Paiza-Cloud.md)<br>
２ 構成の全体像:::::::::::[次のチャプターへ進む](./Overall-image.md)<br>
３　おさらい::::::::::::::[次のチャプターへ進む](./osarai.md)<br>
 　(1) Webアプリケーションとは？？<br>
　 (2) 脆弱性とは？<br>
 　(3) WebにおけるCookieの利用について<br>
４ Webアプリケーションの脆弱性体験<br>
(1) XSS<br>
　　ア　XSSの脆弱性体験<br>
     　[次のチャプターへ進む](./XSS.md)<br>
    イ　XSSの脆弱性対策<br>
    　　[次のチャプターへ進む](./XSS_VulnerabilityCountermeasures.md)<br>
    
(2) CSRF<br>
    ア　CSRFの脆弱性体験<br>
    　　[次のチャプターへ進む](./CSRF.md)<br>
    イ　CSRFの脆弱性対策<br>
    　　[次のチャプターへ進む](./CSRF_VulnerabilityCountermeasures.md)<br>
(3) SQLインジェクション<br>
　　ア　SQLIの脆弱性体験<br>
        [次のチャプターへ進む](./SQLi.md)<br>
    イ　SQLiの脆弱性対策<br>
    　  [次のチャプターへ進む](./SQLi_VulnerabilityCountermeasures.md)<br>

 (3) デイレクトリートラバーサル<br>
    ア　デイレクトリートラバーサルの脆弱性体験<br>
　　　　[次のチャプターへ進む](./Directory_traversal.md)<br>
    イ　デイレクトリートラバーサルの脆弱性対策<br>
     　[次のチャプターへ進む](./Directory_traversal_VulnerabilityCountermeasures.md)<br>
 (4) OSコマンドインジェクション<br>
 　　ア　OSコマンドインジェクションの脆弱性体験<br>
 　　　[次のチャプターへ進む](./OSCommandInjection.md)<br>


５　本環境の使用方法<br>
     [次のチャプターへ進む](./How-to-use.md)<br>
使用する際はPaiza cloudへのアカウント登録が必要です（無料版で問題ありません）<br>

【Paiza cloud】<br>
https://paiza.cloud/ja/<br>

今回使用したコード等はZIP化していますので解凍後、使用してください<br>
scripts配下に以下を格納しています<br>
　　　[使用したコードの格納場所](./script)<br>
１ XSS.zip ：XSS体験<br>
２　
２ CSRF.zip：CSRF体験<br>
３ SQLインジェクション.zip:　SQLi体験<br>
４ QSコマンドインジェクション.zip: OSコマンドインジェクション体験<br>
　〇　ワンライナーWebサーバ.zip : 模擬悪性サイトの起動要領<br>
  
  
■　Paiza CloudはPaiza株式会社の登録商標です。<br>
注意：本資料で紹介したコードを実際のＷｅｂサイト等で運用しないようにしましょう。。<br>
脆弱性が内在しているコードですので、サイトへの侵害、情報漏えいが発生する可能性大です<br>
あくまでも個人のラボ環境で検証などでご使用ください<br>
