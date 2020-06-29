# KubeSphere Console Localization Guide

KubeSphere Console is the web-based UI for [KubeSphere](https://github.com/kubesphere/kubesphere) clusters. It is available in different languages for users around the world with English as the main one. Your contribution to the localization of the Console is highly appreciated and please follow the step below as you start the localization.

## Getting Started

- Fork the [Console Repository](https://github.com/kubesphere/console).
- Start KubeSphere Console by following the [guide](https://github.com/kubesphere/console/blob/master/README.md).

## Localization Step

All the localization files are stored in \console\src\locales. You need to provide localizations based on the source language (English) and submit your target language UI to console\src\locales accordingly.

- Use a tool to open the entire **console** folder, such as [Visual Studio Code](https://code.visualstudio.com/).

- In \console\src\locales, you can see different localizations. If you do not see your language, you need to create that language folder first.

- Copy every file in the **zh** folder to your own language folder and translate the file based on the English in these **zh** files (Please see **Important** below for the reason to copy the **zh** folder instead of the en folder). Namely, replace the Chinese with your own language. For example, you may find the following phrases in app.js:

  ```js
  'Select file': '选择文件',
  'Application Name': '应用名称',
  'Application Version': '应用版本',
  ```

- If you want to provide Spanish localizations for these words, simply delete these Chinese in the single quotation mark and put corresponding Spanish in it based on the English. And these three phrases may look like:

  ```js
  'Select file': 'Seleccione archivo',
  'Application Name': 'Nombre de la aplicación',
  'Application Version': 'Versión de la aplicación',
  ```

- For capitalized keys without English, copy and search the key in the Console folder.

  ![KubeSphere-localization-zhcn](https://ap3.qingstor.com/kubesphere-website/docs/copy-capital-key.png)

- Find the key in \console\src\locales\en and you can see its English text. In your own language folder, delete the Chinese after these capitalized keys and put your translation within the quotation mark based on the English text you just find.

  ![KubeSphere-Localization-en](https://ap3.qingstor.com/kubesphere-website/docs/search-en-text.png)

## Important

- The reason why you copy the zh folder instead of the en folder is that the latter does not contain all the UI texts. Simple UI phrases such as “Select file” are not included in the en folder, which only contains the English UI texts for capitalized keys that are not readable. In other words, simple phrases are already readable English texts so they do not need to be put in the en folder. Admittedly, you can copy all js. files in the en folder to your own language folder and translate capitalized keys. Nevertheless, for individual phrases or words, you have to find them in the console UI and put them one by one in your own language folder, which is too complicated and time-consuming. On the contrary, the zh folder already has all the UI texts. You can use it as a template and work on the localization based on the English UI in it.
- Before you submit your pull requests, you can preview your translation in the UI locally by following the [guide](https://github.com/kubesphere/console/blob/master/README.md).
- Please submit your pull requests to the **dev** branch of the repository.
- Global search and replace is useful for quickly changing words or phrases while it may also lead to unexpected changes, especially those in code that are not the target UI you need to adjust. Please use this feature carefully if you only mean to change the translation instead of the code.
- Normally, the UI text of a feature in the console can be found in its corresponding file. For example, the UI of features related to alerting and monitoring can be found in alerting.js and monitoring.js respectively.
- In each js. file, you can see the UI text is sorted based on their location in the UI. Namely, the UI in the same place of the console is put together so that you can easily find them. This is also recommended for your language as you work on the localization.

## Discussion and Support

- If you find the translation of certain UI cannot be changed on your side (e.g. hard code), please raise an issue.
- If you think any English UI is not clear, you can submit a pull request or raise an issue.
- If you need any help with KubeSphere, you can join us at [Slack Channel](https://join.slack.com/t/kubesphere/shared_invite/enQtNTE3MDIxNzUxNzQ0LTZkNTdkYWNiYTVkMTM5ZThhODY1MjAyZmVlYWEwZmQ3ODQ1NmM1MGVkNWEzZTRhNzk0MzM5MmY4NDc3ZWVhMjE).