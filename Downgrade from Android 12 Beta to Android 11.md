文字版（英文）：

https://nerdschalk.com/how-to-go-back-to-android-11-from-android-12/

文字版（中文）：

https://clickthis.blog/zh-TW/kak-ponizit-versiyu-android-12-beta-3-1-do-android-11-na-telefonah-pixel/

視訊版（Main）：

https://www.youtube.com/watch?v=IjB60yW3ie0

視訊版（Google SDK Driver Install）：

https://www.youtube.com/watch?v=Px_vJZH5oKU



***備份手機所有檔案！一旦進行以下步驟，手機將清空資料及恢復原廠設定。 ***

***自行承擔有關風險***



首先下載工具，共三個檔案。

你想要的系統版本，（以下將用Factory images簡述）。

https://developers.google.com/android/images

SDK Platform

https://developer.android.com/studio/releases/platform-tools

Google SDK Driver （這個確保你電腦可以連接到手機到驅動）：

https://developer.android.com/studio/run/win-usb

*第三點個別情況需要，如你進行以下步驟無法令Fastboot改為Unlock，則需要執行第三點，將會在本文最後補充概述。





**【A】下載檔案並解壓縮**

1.解壓縮SDK Platform。

2.解壓縮Factory images（出廠映像），開啟至目錄最後的文件，並將其複製在步驟1文件的「platform-tools」下。



**【B】啟用 OEM 解鎖和 USB 偵錯**


開啟手機「設定」（Setting），「關於手機」（About Phone），點擊內部版本號七次。輕按七次後，螢幕底部將出現一個對話框，提示「您現在是開發人員」。

Now you need to head to Settings > System > Advanced > Developer options (you may need to expand a hidden menu for this).

2. 首先啟用 USB 偵錯，然後啟用 OEM 解鎖，之後會出現一則訊息，要求您按一下啟用。

Before we are ready to continue, you will need to scroll down and enable “OEM unlocking” as this is integral for further steps. Now scroll slightly further down to the “Debugging” section and tap the “Allow USB debugging” option.


3. 將您的手機連接到您的 PC，它會要求您的手機授權，因此請確保您啟用 USB 偵錯。 （如果你沒有看見提示，則重新連接一次手機，接著會提示你是否允許開啟USB調試，點擊不再詢問/永遠允許，並點擊允許。）

4. 開啟platform-tools資料夾，在網址列位置輸入「CMD」（或按Ctrl+右鍵，選擇執行指令視窗），開啟執行指令視窗。

5.你可以輸入“adb devices”，如果成功連接，會出現List of devices attached和一串Code，如果顯示“未經授權”或其他錯誤訊息（例如：Waiting for any device），你則需要驅動Google SDK Driver（參考本文最後補充）。



**【C】解鎖引導程式**

6. 在CMD視窗輸入「adb reboot bootloader」。

7. 接著繼續輸入「fastboot flashing unlock」。不要關閉CMD視窗！

![Image](https://github.com/user-attachments/assets/6bb5a8eb-061c-42e9-a5ba-29b408e8955d)

8. 你的手機此時應該跳進Fastboot畫面，並顯示Unlock的狀態。使用音量鍵，選擇“Unlock the BootLoader”，按下Power鍵，確認選擇。

9.此時，你手機已恢復出廠設定（但還是Android 12），跳過所有重置新系統設定（沒用的，之後會再刷一遍，不需要連網）。然後，重新進行步驟1-3的動作。

10. 在CMD窗口，再次輸入「adb reboot bootloader」。

11. 確保你已經將Factory images（出廠映像）解壓縮在「platform-tools」下！在CMD窗口，輸入“flash-all”。

![Image](https://github.com/user-attachments/assets/de03a8e0-8a41-4e66-9eb0-07a87674538a)

現在，手機正安裝Android11.等待大約2-5分鐘時間，不要關閉窗口，直到窗口出現“Press any key to exit...”，則安裝完成。



**【D】重新鎖定引導程式**

12. 此時，你手機再次恢復出廠設定（現在！就是Android 11了！），跳過所有重置新系統設定（沒卵用的，之後會再刷一遍，不需要連網）。然後，重新進行步驟1-3的動作。

13. 開啟platform-tools資料夾，在網址列位置再次輸入「CMD」（或按Ctrl+右鍵，選擇執行指令視窗），開啟執行指令視窗。

14. 在CMD窗口，再次輸入「adb reboot bootloader」。

15. 這次執行重新鎖定，我們輸入「fastboot flashing lock」。

16. 此時，跳進Fastboot畫面，使用音量鍵，選擇“lock the BootLoader”，按下Power鍵，確認選擇。

17. 你手機又恢復出廠設置，此時你終於可以認真設定新系統設定了！

【完】



**【補充】驅動Google SDK Driver**


1. 下載Google USB Driver，連接你到手機到電腦。

2. 解壓縮，並開啟至最後檔案的位置，複製資料夾位址。

3. 啟動裝置管理員（Device Manager）。

![Image](https://github.com/user-attachments/assets/b4293950-b0a2-4f25-a0cd-44677fca218c)

在其他設備，找到你的手機型號，右鍵，點擊「更新驅動」。

“瀏覽”>>“在我的電腦裡選擇資料夾”>>“All the Devices”>>“下一步”>>“Have Disk”>>貼上剛才複製的位址 >>“瀏覽”，選擇檔案“Android-WinUSB”

![Image](https://github.com/user-attachments/assets/c98216a4-a643-4ccf-b68e-c33391233246)

“確定”>> 點擊“Android BootLoader Interface”>> 下一步 >>彈出允許安裝提示窗，按下“安裝”，完成後關閉安裝。

4. 此時你進入CMD窗口，輸入“fastboot devices”，將會看見一串Code。表示已經連接上手機了。

回到步驟6，繼續執行操作。

