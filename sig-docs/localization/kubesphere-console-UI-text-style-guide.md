# KubeSphere Console UI Text Style Guide

The KubeSphere console provides the web-based UI for [KubeSphere](https://github.com/kubesphere/kubesphere) clusters. It is available in different languages for users around the world with English as the main one. This document includes major guidelines related the English UI text of the console. For more information about how to localize the console text, refer to [KubeSphere Console Localization Contributor Guide](https://github.com/kubesphere/community/blob/master/sig-docs/localization/how-to-localize-console.md).

## Getting Started

- Fork the [Console Repository](https://github.com/kubesphere/console).
- Access and build the KubeSphere console locally by following the [guide](https://github.com/kubesphere/console/blob/master/README.md).

## UI Text Capitalization 

There are mainly two ways for UI text capitalization depending on where it is located:

### Headline-style capitalization

Capitalize every word in the text, except:

- Infinitives (in, an, to)

- Prepositions (unless it is the first or last word)

- Conjunctions (and, or)

- Articles (unless it is the first or last word)

Use headline-style capitalization for the following UI elements:

- Chart titles
- Dialog box titles
- Icon labels
- Menu items (both menu bar and context menus)
- Menu titles
- Page titles
- Button labels
- Section headings
- Table column headers
- Tab titles
- Table titles
- Toolbar buttons
- Window titles
- Field titles
- List box, drop-down list, and combination box entries

### Sentence-style capitalization

You only need to capitalize the first word for sentence-style capitalization. Use sentence-style capitalization for the following UI elements:

- Check box text
- File names
- Group box text
- Hover help text
- Input hints
- List box labels
- Messages (information, warning, and error)
- Page instructions or descriptions
- Progress bar label
- Radio button labels
- Status bar text

> The above rules do not apply to words or fields that are written conventionally with a specific capitalization way, such as macOS, PersistentVolumeClaim, and restartPolicy and allowVolumeExpansion. These words should be written in the way as they are known to general users.

### Punctuations

Use a **period** or a **conjunction** between two **complete** sentences.

| Do                                                           | Don't                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| The component has been installed. You can now use the feature. | The component has been installed, you can now use the feature. |
| Check the status of the component. You can see it is running normally. | Check the status of the component, you can see it is running normally. |
| Check the status of the component, and you can see it is running normally. | Check the status of the component, you can see it is running normally. |

### Alert guidelines

Keep alerts simple and short.

- Success

  Successfully created Deployment

  Workload successfully updated

- Info

  Updating volume snapshot

  Creating volume XXX

- Warning

  Status check failed

  Insufficient privilege level exists to view user information

- Danger

  Unable to create the volume

## Steps

English UI source files are stored in `console/src/locales/en`.

1. Use a tool to open the entire **console** folder, such as [Visual Studio Code](https://code.visualstudio.com/).

2. Use the global search function to locate the UI text that you want to change. Note that you need to change both the key and value. If the UI text is referenced in the code (such as `t('Cluster Node Status')`), it must be changed as well.

   ```js
     'Select file': 'Select file',
     'Application Name': 'Application Name',
     'Application Version': 'Application Version',
      FILE_UPLOAD_MAX: 'The file size cannot exceed 2M.',
   ```

3. Double check your change on the console.

## Important

- Before you submit your pull requests, you can preview your UI text by following the [guide](https://github.com/kubesphere/console/blob/master/README.md).

- Please submit your pull requests to the **master** branch of the **console** repository.

- Global search and replace is useful for quickly changing words or phrases while it may also lead to unexpected changes, especially those in code that are not the target UI you need to adjust. Please use this feature carefully.

- Normally, the UI text of a feature in the console can be found in its corresponding file. For example, the UI of features related to alerting and monitoring can be found in alerting.js and monitoring.js respectively.

- A same UI string may be used or referenced in different places. UI strings should be consistent while their singular or plural forms may be different depending on the context. If the same UI string is referenced in the code while in fact the UI text should be different, submit an issue to the console repository. 

- UI texts of the login page are stored in `server/locales`.

- If you change the referenced source English text in the code, make sure it is also changed in `console/src/locales/en` as well as the folder of other languages. For example, you use the global search function for the string "Cluster Node Status, and here is the result:

  ![search-result-example](https://ap3.qingstor.com/kubesphere-website/docs/20210308110524.png)

  You must change all the 6 places above to your desired UI text. Note that the sixth place is the UI text referenced in the code by all the languages, including English itself. If the change is a major one, make sure the localization of other languages is changed to English temporarily, or users may see the wrong localized version for the UI text.
