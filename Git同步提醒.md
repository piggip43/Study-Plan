# Git同步提醒

> 切換電腦前，一定要先在原電腦完成`commit`和`push`。`commit`只會把修改保存於目前電腦；只有完成`push`，另一台電腦才下載得到最新內容。

## 一、開始修改前

若這個資料夾已經連接GitHub，開始工作前先取得遠端的最新版本：

```powershell
Set-Location -LiteralPath "C:\Users\flyinfantasy\Documents\HUNGRU\讀書計畫"
git pull --ff-only
```

如果`git pull`顯示衝突，先不要繼續修改或強制覆蓋，應先處理兩台電腦的版本差異。

## 二、修改完成或切換電腦前

```powershell
Set-Location -LiteralPath "C:\Users\flyinfantasy\Documents\HUNGRU\讀書計畫"

git status
git add --all
git commit -m "簡短說明這次修改"
git push
```

完成後再檢查一次：

```powershell
git status
```

看到工作目錄沒有未提交修改，且分支已與`origin/main`同步，才代表這台電腦的變更已安全上傳。

## 三、在另一台電腦繼續工作

若另一台電腦已經下載過這個儲存庫：

```powershell
Set-Location -LiteralPath "另一台電腦上的讀書計畫資料夾"
git pull --ff-only
```

若另一台電腦尚未下載過：

```powershell
git clone https://github.com/piggip43/Study-Plan.git
Set-Location -LiteralPath ".\Study-Plan"
```

## 四、最簡單的記法

1. 開始工作前：`git pull --ff-only`
2. 修改完成後：`git add --all`
3. 保存本機版本：`git commit -m "修改說明"`
4. 上傳至GitHub：`git push`
5. 確認同步狀態：`git status`

## 五、新增檔案後是否要提交

是。新增、修改或刪除檔案後，只要希望GitHub及其他電腦取得這些變更，就要再次執行`add`、`commit`和`push`。例如本提醒檔建立後，可執行：

```powershell
git add --all
git commit -m "新增Git同步提醒"
git push
```
