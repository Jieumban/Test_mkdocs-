# About Mkdocs

- Contributors : 裕禾
- last updated : 20240805

---

Mkdocs(Markdown Documents)，是一個靜態網頁產生器，可以透過簡單的方式將markdown文件整理成有層次且美觀的網站。

目前我使用Materials for Mkdocs來架設CO2024的課程網站，Mterials是Mkdocs的一個主題，透過github或gitlab發佈repository來進行管理，並利用ci工具，讓repo在git push後可以重新deploy並更新網頁內容。

mkdocs.yml是一個YAML文件，同時也作為此repo的核心，對網站進行配置及管理，包含背景顏色、連結hightlight等功能，以及網頁的架構，文件的階層關係也是在mkdocs.yml的 `nav:` 進行設定。

Mkdocs的 `nav:` 預設將docs做為根目錄，因此在 mkdocs.yml 上只須寫上相對路徑就好。

目前支援功能<br>
    - 一般模式與夜間模式切換
    - 關鍵字搜尋欄

---

## 新增頁面
若是需要新增頁面，請在mkdocs.yml下的 `nav:` 區塊下新增 `- 頁面名稱: XX.md`，之後到docs資料夾下新增對應的 `XX.md` 進行網頁內容的編寫，文件支援多數Markdown語法。

## 更新網站內容
目前在 `.\docs\labs` 下已建立lab1~lab8的markdown文件，可以在此進行教材的更新，需要編輯或新增內容的，只需要將repo下載到本地端編輯，完成後再push上來就好。<br>
在進行文件編輯時，有時Markdown文件並不會自動幫你分段，若遇到相關問題，有三種解決方式

- 在欲分段之段落後面按兩次空白鍵
- 在欲分段之段落後面加上 `<br>`
- 在兩段落間多加入一個空行

## 圖片上傳
在docs底下有images資料夾，專門存取文件上需要引用到的圖片，為了避免混亂，我會希望在各自的文件都有自己的目錄來存圖片，目前先放了lab1~lab8的資料夾，其他頁面有需要的話可以自己新增，插入時記得該文件與圖片的相對路徑。

```
![example](./images/test000.jpg)
```
範例
![example](./images/test000.jpg)