---
title: 將數據由 Python 儲存至 Google Sheet
date: 2022-09-10T11:27:42+08:00
draft: true
author: HaNg~
url: /2022/09/10/python-to-google-sheet/
categories:
  - 網誌
tags:
  - Python
  - Google Sheet
  - Data
  - Visualization
---

除住伺服器要更新，寄存係伺服器嘅 tasks 都要搵個地方搬，因為新的地方唔再有 [MariaDB][1] 可以用。呢家手頭上有一個 task 係每個鐘都行，係網上爬啲 data 之後執靚寫落 database，`INSERT` 多而 `SELECT` 少，集齊一大堆數據再會下載落嚟分析。其實又冇 `JOIN` 又唔太需要 SQL operation，真係唔需要用到 [relational database][2]，花錢開多部機行 Database 就好唔抵。

<!--more-->

其間都有考慮過唔同嘅可能性︰

 - [AWS Lambda][3] and [AWS S3][4]
 - [MongoDB atlas][5]
 - [DigitalOcean App Platform][6]
 - New VPS server

後來，見到有中文 blogger 介紹[解析如何串接Google Sheet試算表寫入爬取的資料][7]，發現佢先係我呢個情況最好嘅替代方案。為左避免對方搬家或者刪除 blog，我決定將重點抄一次落嚟。

### A. 啟用金Google Sheet API

 1. 前住 [Google API Console][8] 並登入 Google Account
 2. 為你的程序 **新增專案**
 3. 按 **建立** 完成新增專案
 4. 在 **快速存取** 選擇 **API 和服務**
 5. 再選擇 **啟用 API 和服務**
 6. 搜索並選擇 **Google Sheets API**，並點擊 **啟用**

### B. 建立 Google Sheets API 憑證

 1. 在 **API 和服務** 中選擇 **憑證**
 2. 選擇 **建立憑證**
 3. 資料類型選擇 **應用程式資料**
 4. 選擇 **不搭配使用** Compute Engine、Kubernetes Engine、App Engine 或 Cloud Functions
 5. 建立一個 **服務帳戶的名稱**，系統會生成一個 email address
 6. 完成後選擇剛才建立的名稱，再按 **金鑰** 新增一個 `JSON` 檔案予 Python 使用

### C. 建立 Google Sheet

 1. 建立一個全新的 Google Sheet
 2. 在 URL address 中尋找 Google Sheet unique ID
   - `https://docs.google.com/spreadsheets/d/<unique_id>/edit#gid=0`
 3. 在已下載的 `JSON` 檔案尋找 email address，並把 Google Sheet 共用予該 email address

### D. 將數據提交至 Google Sheet

 1. 先安裝所需要的 Python library

    ```bash
    pip install gspread oauth2client
    ```
 
 2. 將下載的 `JSON` 檔案命名為 `credentials.json`
 3. 在 Python 中置入以下內容，以便寫入 Google Sheet

    ```python
    import gspread
    from oauth2client.service_account import ServiceAccountCredentials

    from datetime import date, datetime

    def gsheet(data):
        scopes = ["https://spreadsheets.google.com/feeds"]
        
        credentials = ServiceAccountCredentials.from_json_keyfile_name(
            "credentials.json", scopes)
        
        client = gspread.authorize(credentials)
        
        sheet = client.open_by_key(
            "<unique_id>").sheet1
        
        for i in range(10):
            sheet.append_row((
                datetime.now().strftime('%Y-%m-%d %H:%M:%S'), 
                data['col1'], 
                data['col2'], 
                data['col3']
            ))
    ```

 4. 呼叫 Python function `gsheet` 新增數據到 Google Sheet

詳情或者想睇圖，可以返回 [Mike][7] 嘅文章了解下。


 [1]: https://mariadb.org/ "MariaDB Foundation"
 [2]: https://en.wikipedia.org/wiki/Relational_database "Relational database"
 [3]: https://aws.amazon.com/tw/lambda/
 [4]: https://aws.amazon.com/tw/s3/
 [5]: https://www.mongodb.com/cloud/atlas/
 [6]: https://www.digitalocean.com/products/app-platform
 [7]: https://www.learncodewithmike.com/2020/08/python-write-to-google-sheet.html
 [8]: https://console.developers.google.com/