# Deprecated, Ublacklist now supports Searx engine. I also don't use searx anymore since the public instances are having a lot of issues and the dev team is not very friendly.


### SearchBlocklist

Its a fork of:
https://iorate.github.io/ublacklist

With the added Searx engine support.

## Supported search engines

This extension is available in the below search engines.
| | Web | Images | Videos | News |
| -------------------------------| ------------------ | ------------------ | ------------------ | ------------------ |
| Google | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Google (iOS) | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Bing | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Bing (iOS) | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| DuckDuckGo | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| DuckDuckGo (iOS) | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Ecosia | :heavy_check_mark: | | | |
| Ecosia (iOS) | :heavy_check_mark: | | | |
| Qwant | :heavy_check_mark: | :heavy_check_mark: | \*1 | :heavy_check_mark: |
| Qwant (iOS) | :heavy_check_mark: | :heavy_check_mark: | \*1 | :heavy_check_mark: |
| Startpage | :heavy_check_mark: | | :heavy_check_mark: | :heavy_check_mark: |
| Startpage (iOS) | :heavy_check_mark: | | :heavy_check_mark: | :heavy_check_mark: |
| Searx \*2 | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |

\*1 Works only if you turn off "Always play videos on Qwant.com".

\*2 Only for _public instances that support google_ (check https://searx.space/).

## For developers

### Build

To build this extension, [Node.js](https://nodejs.org/en/) and [Yarn](https://yarnpkg.com/) are required.

```shell
git clone https://github.com/masterofobzene/SearchBlocklist.git

cd SearchBlocklist

yarn

# yarn build <browser:=chrome> <mode:=development> <typecheck:=notypecheck>
yarn build firefox production
```

Before opening a pull request, you should make sure that `yarn lint`, `yarn test`, and `yarn build-all` pass.

```shell
yarn lint
# Some lint errors can be fixed automatically
# yarn fix

yarn test

yarn build-all
```

**NOTE:** The API keys and secrets for the sync feature are not included in this repository. To develop the sync feature, set your own API keys and secrets in the `.env` file.

```
DROPBOX_API_KEY=...
DROPBOX_API_SECRET=...
GOOGLE_DRIVE_API_KEY=...
GOOGLE_DRIVE_API_SECRET=...
```

### Locale

To add a locale,

1. Determine an ISO language code such as `en` referring to [kLanguageInfoTable](https://src.chromium.org/viewvc/chrome/trunk/src/third_party/cld/languages/internal/languages.cc).
1. Copy `src/locales/en.json.ts` to `src/locales/${languageCode}.json.ts` and translate entries.
1. Open `src/scripts/dayjs-locales.ts` and import the dayjs locale.
1. To localize description and screenshots on web stores, create `web-store-assets/${languageCode}/` and add files.
   - Screenshot localization is available only on Chrome Web Store.
   - Screenshots should be 1280x800.

