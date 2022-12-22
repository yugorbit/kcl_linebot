# kcl_linebot

```javascript
function doPost(e) {
  let token = "トークンの文字列";
  let eventData = JSON.parse(e.postData.contents).events[0];
  let replyToken = eventData.replyToken;
  let userMessage = eventData.message.text;
  let replyMessage = "";
  let url = "https://api.line.me/v2/bot/message/reply"

  if(userMessage == "工学部") {
    replyMessage = "工学部は 福岡県北九州市戸畑区仙水町1-1 です。";
  } else if(userMessage == "情報工学部") {
    replyMessage = "情報工学部は 福岡県飯塚市川津680-4 です。";
  } else {
    replyMessage = "「"+userMessage+"」という学部はありません。";
  }

  let payload = {
   'replyToken': replyToken,
   'messages': [{
       'type': 'text',
       'text': replyMessage
     }]
  };

  let options = {
    'payload' : JSON.stringify(payload),
    'myamethod'  : 'POST',
    'headers' : {"Authorization" : "Bearer " + token},
    'contentType' : 'application/json'
  };

  UrlFetchApp.fetch(url, options);
}

```
