# KubeSphere Console Localization Guide

KubeSphere Console is the web-based UI for [KubeSphere](https://github.com/kubesphere/kubesphere) clusters. It is available in different languages for users around the world with English as the main one. Your contribution to the localization of the Console is highly appreciated and please follow the step below as you start the localization.

## Getting Started

- Fork the [Console Repository](https://github.com/kubesphere/console).
- Start KubeSphere Console by following the [guide](https://github.com/kubesphere/console/blob/master/README.md).

## Localization Step

Localization files are stored in console/src/locales. You need to provide localizations based on the source language (English) and submit your target language UI to console/src/locales accordingly.

1. Use a tool to open the entire **console** folder, such as [Visual Studio Code](https://code.visualstudio.com/).

2. In console/src/locales, you can see different localizations. If you do not see your language, you need to create that language folder first.

3. Copy every file in the **en** folder to your own language folder and translate the file based on the English UI text. Namely, replace the English value with your own language. For example, you may find the following content in app.js:

  ```js
  'Select file': 'Select file',
  'Application Name': 'Application Name',
  'Application Version': 'Application Version',
   FILE_UPLOAD_MAX: 'The file size cannot exceed 2M.',
  ```

4. If you want to provide Spanish localizations for them, simply delete the English value in the single quotation mark and put corresponding Spanish in it based on the English. And the localization may look like:

  ```js
  'Select file': 'Seleccione archivo',
  'Application Name': 'Nombre de la aplicación',
  'Application Version': 'Versión de la aplicación',
   FILE_UPLOAD_MAX: 'El tamaño del archivo no puede exceder los 2M.',
  ```

## Add Your Language to Console

Please follow the step below to make your language available in the web console.

1. In **config.yaml** in the folder **server**, you can find supported language options under **supportLangs** as below:

   ```js
   supportLangs:
     - label: '简体中文'
       value: 'zh'
     - label: 'English'
       value: 'en'
   defaultLang: 'en'
   ```

   In this list, add your own language name for **label** and put the corresponding two-letter language code for **value**.

2. In **i18n.js** in src/core, navigate to **const getLocales**:

   ```js
   const getLocales = {
     zh: lazy(() => import(/* webpackChunkName: "locales-zh" */ `../locales/zh`)),
     en: lazy(() => import(/* webpackChunkName: "locales-en" */ `../locales/en`)),
   }
   ```

   Add your own language code to the list. For example, you can add Turkish localization option (tr) by putting the following code to the list:

   ```js
   tr: lazy(() => import(/* webpackChunkName: "locales-tr" */ `../locales/tr`)),
   ```

3. Restart the web console. In User Settings in the drop-down list at the top right corner, you can find your language option available in **Language** list.

## Important

- Before you submit your pull requests, you can preview your translation in the UI locally by following the [guide](https://github.com/kubesphere/console/blob/master/README.md).
- Please submit your pull requests to the **master** branch of the **console** repository.
- Global search and replace is useful for quickly changing words or phrases while it may also lead to unexpected changes, especially those in code that are not the target UI you need to adjust. Please use this feature carefully if you only mean to change the translation instead of the code.
- Normally, the UI text of a feature in the console can be found in its corresponding file. For example, the UI of features related to alerting and monitoring can be found in alerting.js and monitoring.js respectively.
- In each js. file, you can see the UI text is sorted based on their location in the UI. Namely, the UI in the same place of the console is put together so that you can easily find them. This is also recommended for your language as you work on the localization.
- UI texts of the login page are stored in server/locales. Please create a properties file for your localization with your two-letter language code as the name.

## Discussion and Support

- If you find the translation of certain UI cannot be changed on your side (e.g. hard code), please raise an issue.
- If you think any English UI is not clear, you can submit a pull request or raise an issue.
- If you need any help with KubeSphere, you can join us at [Slack Channel](https://join.slack.com/t/kubesphere/shared_invite/enQtNTE3MDIxNzUxNzQ0LTZkNTdkYWNiYTVkMTM5ZThhODY1MjAyZmVlYWEwZmQ3ODQ1NmM1MGVkNWEzZTRhNzk0MzM5MmY4NDc3ZWVhMjE).