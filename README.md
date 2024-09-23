[https://github.com/AsemAlhaidary/hexo-generator-readtime](https://github.com/AsemAlhaidary/hexo-generator-readtime) 의 fork 버전으로 한국어 번역 일부 수정 및 전역 언어 설정 버그 수정 
(node 22 및 npm 10 기준)

# hexo-generator-readtime

[HEXO](https://github.com/hexojs/hexo) package that provides analytics on the read time to review the post. *Supports 48 languages!* Can add or override langProfile defaults.

## Install

``` bash
$ npm install https://github.com/MinsuChae/hexo-generator-readtime.git
```

📝 When `defaultTime` is set to "`auto`," it will calculate the fuzzy time based on the least "count" time for `fuzzyTime.time_unit`. Example: 578sec becomes "about 10 minutes".
If you define `defaultTime` as "seconds", "minutes", etc., the time returned is more precise whereas "auto" will provide a very rough estimation.

## How to use

After you have installed this plugin, it will run anytime you run `hexo server` or `hexo generate`.

readTime will read the `lang` value in your front-matter to select the correct language profile. If this value is missing, it will attempt to read the `_config.yml` setting. If both of these are missing, then it will default to `en` (English).

It updates the front-matter of your posts to include the analytics data. The following parameters are added:

| parameter | description |
| --- | --- |
| *readTime* | String that represents the estimated time to read the article. Printed in the detected language's native text. |
| *imgCount* | Count of images found in the file. |
| *vidCount* | Count of videos detected in the file. |
| *wordCount* | Count of words in the file. This works very well for non-Asian languages. Some languages don't employ the space character as a word boundary. For Asian languages such as Chinese, Korean, Japanese, and Vietnamese, another method is required to create word tokens. |
| *wsCount* | Count of white-space characters detected in the file. This is only useful for non-Asian languages. |
| *charCount* | Letters detected for the given language in the file. |
| *cbCount* | Count of code blocks in the file. |

👉🏻 Note: it only reads the posts from the `/source/_posts/` folder. You can reference these values in your EJS template files from the object `post`. For example: `<%= post.readTime %>`. This plugin updates both in-memory `post` object and the markdown file.

Original package is [here](https://github.com/AsemAlhaidary/hexo-generator-readtime)
