Original prompt: 我說的是如果選項填錯的話,上面跳出一個彈出式的小框框,那這一個請你把它按下確認後,不要直接回到主頁,而是讓它可以回到選擇題目的那一個區域。另外那個履行後記有一些markdown沒有很清楚的 而且按下履行後記的時候沒有立刻觸發

- 檢查到錯誤選項目前仍會 `alert` 後直接 `location.reload()`。
- 檢查到 `#ending-notes` 的 `z-index` 是 120，但首頁 `#start-overlay` 是 200，會導致首頁點 `旅行後記` 時被蓋住。
- 這次要修三件事：錯誤答案留在原題、後記面板抬高層級並重設捲動、補強 Markdown 呈現。
- 已改成錯誤答案只跳提示，不再回首頁，確認後會停留在原本題目區域重新選。
- 已把 `#ending-notes` 提升到 `z-index: 260`，並在開啟時把 `#ending-notes-card` 捲回最上方。
- 已用 skill 內建 Playwright client 測試首頁 `.start-secondary-btn`，確認 `旅行後記` 會正常浮到首頁上層並顯示完整版內容；截圖位於 `output/web-game-travel-notes/shot-0.png`。
- 額外嘗試用臨時 Node 腳本驗證錯誤選項互動，但工作目錄下無法直接載入 `playwright` 套件，因此這一點沒有做第二套自訂腳本驗證。
- 補充判斷：GitHub 遠端已同步，但專案根目錄沒有 `index.html`，這會讓 Vercel 在 `/` 找不到預設入口。
