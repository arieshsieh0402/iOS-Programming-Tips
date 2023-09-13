# Xcode 相關

## Xcode 不支援最新版本的 iOS

這個問題的解法有兩個：
1. 更新你的 Xcode
2. 新增 DeviceSupport

第一種作法當然是最直接的方法，但若因應開發穩定或有其他需求，而暫時不考慮更新 Xcode 版本的話，那便要採取第二種做法。

第二種作法是去新增最新版本的 iPhone DeviceSupport 檔案，取得方式為抓取最新版本的 Xcode，你下載的檔案副檔名可能是 `.xip` 或是 `.dmg`，但這不影響。對檔案右鍵，選取 **Show Package Content** 後，在以下路徑可以找到最新版本的檔案。

>/Contents/Developer/Platforms/iPhoneOS.platform/DeviceSupport

取得最新版本的 iPhone DeviceSupport 檔案後，便可以將檔案複製到本機舊版 Xcode 的以下路徑資料夾後，記得重新啟動 Xcode，就可以支援最新版本的 iOS 了。

>/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/DeviceSupport

可以在 finder 上方狀態列的 Go，選取 Go to Folder 中複製以上路徑。

## project.pbxproj 的檔案位置

可以從專案資料夾，對專案的 .xcodeproj 檔案右鍵點選 Show Package Content

或是從 Sourcetree 去查找

