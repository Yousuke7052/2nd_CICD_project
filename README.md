# 2nd_CICD_project
Practice CICD project by myself

設計了一個適用於無經驗，並從0開始搭建的CICD單人小型實踐項目，並考慮了低成本，同時也盡量避免再上傳GitHub時需要敏感信息
的操作，對於不會前後端語言與YAML文件配置等等的人也盡可能友好，提供每一個階段每一個動作要輸入的指令或配置文件代碼等

項目目標：配置阿里云DevOps平台上的CI/CD流水线，自动化构建文本文件项目。当有新的提交时，流水线将自动运行一个脚本来打印出文件内容。

若使用阿里云云效DevOps，無須.github/workflows下的yml文件即可關聯至DevOps(透過webhook)

1-1.
創建流水線源->開啟代碼源觸發->WebHook填入URL(在觸發設置內有，選擇流水線源不選通用)
觸發設置->WebHook不打勾(若打勾適用於第三方以外如自建的倉庫)
1-2.
GitHub目標倉庫下->Setting->左邊欄位找Webhooks->Add webhook->Payload URL為剛剛的WebHook與選擇application/json
1-3.
到代碼倉庫頁面->選擇目標項目倉庫如:2nd_CICD_project->設置->Webhooks->新建並把URL跟Token填入

此為代碼源觸發設置流程
同時，依據創建的流水線生成的webhookURL來控制代碼關聯/對應哪一條流水線

2-1.在創建的流水線執行命令中，直接輸入./build.sh即可，其他都不用輸入了
2-2.build.sh執行，可以在日志看到執行成功後產生的對應結果

無須工作流文件只需關聯webhook，剩下就是代碼提交測試，將自動執行流水線
