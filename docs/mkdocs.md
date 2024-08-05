# About Mkdocs

- Contributors : 裕禾
- last updated : 20240805

Mkdocs(Markdown Documents)，是一個靜態網頁產生器，可以透過簡單的方式將markdown文件整理成有層次又美觀的網站。

目前我使用Materials for Mkdocs來架設CO2024的課程網站，Mterials是Mkdocs的一個主題，透過github或gitlab發佈repository來進行管理，並利用ci工具，讓repo在git push後可以自動更新網頁內容。

mkdocs.yml是一個YAML文件，同時也作為此repo的核心，對網站進行配置及管理，包含背景顏色、連結hightlight等功能，以及網頁的架構，page的階層關係也是在mkdocs.yml的`nav:`設定。

Mkdocs會預設將docs做為根目錄，因此文件只須寫上相對路徑就好。

## 新增頁面
若是需要新增頁面，請在mkdocs.yml下的 `nav:` 區塊下新增 `- 頁面名稱: XX.md`，之後到docs資料夾下新增對應的XX.md 進行網頁內容的編寫，多數Markdown語法都支援。

## 更新網站內容
目前在`.\docs\labs下已建立lab1~lab8的markdown文件，可以在此進行教材的更新，需要編輯或新增內容的，只需要將repo下載到本地端編輯，完成後再push上來就好。