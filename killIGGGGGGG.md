SAFARI之前登入ig的小帳、剛剛要登threads要用大帳結果一直卡在小帳

幹很白痴煩死了

失敗的紀錄：

問grok，先用終端機刪，目標：「我從來沒有在safari登入過ig一樣」

執行步驟（照順序做）：

先強制關閉 Safari（重要！不然檔案被鎖住清不掉）
在 Terminal 貼這行，按 Enter：Bashkillall -9 Safari
只清除 IG / Threads / Meta 的所有資料
一次貼下面這些指令（一行一行貼，按 Enter）：Bash# 清除 IG、Threads、Meta 相關的 Cookies
rm -rf ~/Library/Cookies/*instagram* 
rm -rf ~/Library/Cookies/*threads* 
rm -rf ~/Library/Cookies/*facebook* 
rm -rf ~/Library/Cookies/*meta*

# 清除 Website Data（登入狀態最主要的地方）
find ~/Library/Safari/WebsiteData -name "*instagram*" -o -name "*threads*" -o -name "*facebook*" -o -name "*meta*" 2>/dev/null | xargs rm -rf

# 清除 Safari 的 LocalStorage 和 Databases 裡的 IG 資料
find ~/Library/Safari/LocalStorage -name "*instagram*" -o -name "*threads*" 2>/dev/null | xargs rm -rf
find ~/Library/Safari/Databases -name "*instagram*" -o -name "*threads*" 2>/dev/null | xargs rm -rf

# 清除 Cache 裡的 IG 相關
find ~/Library/Caches -name "*instagram*" -o -name "*threads*" -o -name "*com.apple.Safari*" 2>/dev/null | xargs rm -rf
清空垃圾桶（把剛刪的檔案徹底移除）
右鍵垃圾桶 → 清空垃圾桶，或在 Terminal 輸入：Bashrm -rf ~/.Trash/*
重新開 Safari
直接打開 Safari → 去 instagram.com
它現在應該像第一次登入一樣，完全沒有任何 IG 登入記錄（主帳和小帳的殘留都清光了）。

效果確認：

等同 Safari 裡「從來沒登入過 IG / Threads」。
舊小帳卡住的問題會徹底消失。
你之後要重新用主帳登入，然後再加入小帳（Switch accounts 就會乾乾淨淨）。

小提醒：

清完後主帳也會被登出，所以要重新輸入密碼登入。
如果你小帳很久沒用，建議先用手機 IG App 登入小帳 → 設定 → 帳號中心 → 設定獨立密碼，之後電腦切換才順。
這不會影響手機上的 IG，也不會影響 Safari 裡其他網站（如 Google、YouTube 等）。

###
