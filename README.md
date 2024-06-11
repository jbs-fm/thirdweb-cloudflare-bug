# thirdweb v5 - cloudflare runtime issue

## Setup

- create cloudflare + [remix](https://remix.run/) basic project: `bun create cloudflare@2.5.0`
- install thirdweb and use the provider

## Problems

- Cannot use cloudflare worker runtime (locally, or remotely)
  - `bun run build` works
  - `bun run start` fails (error compiling worker)
  - `bun run deploy` fails (error compiling worker)

## Notes

- doesn't work with npm, pnpm either

<details>
<summary>cli output error compiling worker</summary>

```sh
Compiling worker to "/Users/jbs-fm/git/thirdweb-cloudflare-bug/.wrangler/tmp/pages-r449qs/functionsWorker-0.2547805039617401.mjs"...
✘ [ERROR] 14 error(s) and 0 warning(s) when compiling Worker.



✘ [ERROR] Could not resolve "@coinbase/wallet-mobile-sdk"

    ../node_modules/thirdweb/dist/esm/wallets/coinbase/coinbaseMobileSDK.js:1:26:
      1 │ import { configure } from "@coinbase/wallet-mobile-sdk";
        ╵                           ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  You can mark the path "@coinbase/wallet-mobile-sdk" as external to exclude it from the bundle, which will remove this error.


✘ [ERROR] Could not resolve "@coinbase/wallet-mobile-sdk/build/WalletMobileSDKEVMProvider"

    ../node_modules/thirdweb/dist/esm/wallets/coinbase/coinbaseMobileSDK.js:10:4:
      10 │     "@coinbase/wallet-mobile-sdk/build/WalletMobileSDKEVMProvider"...
         ╵     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  You can mark the path "@coinbase/wallet-mobile-sdk/build/WalletMobileSDKEVMProvider" as external to exclude it from the bundle, which will remove this error. You can also add ".catch()" here to handle this failure at run-time instead of bundle-time.


✘ [ERROR] Could not resolve "aws-amplify"

    ../node_modules/thirdweb/dist/esm/wallets/in-app/native/auth.js:1:21:
      1 │ import { Auth } from "aws-amplify";
        ╵                      ~~~~~~~~~~~~~

  You can mark the path "aws-amplify" as external to exclude it from the bundle, which will remove this error.


✘ [ERROR] Could not resolve "expo-web-browser"

    ../node_modules/thirdweb/dist/esm/wallets/in-app/native/auth.js:2:28:
      2 │ import * as WebBrowser from "expo-web-browser";
        ╵                             ~~~~~~~~~~~~~~~~~~

  You can mark the path "expo-web-browser" as external to exclude it from the bundle, which will remove this error.


✘ [ERROR] Could not resolve "aws-amplify"

    ../node_modules/thirdweb/dist/esm/wallets/in-app/native/helpers/auth/cognitoAuth.js:1:30:
      1 │ import { Amplify, Auth } from "aws-amplify";
        ╵                               ~~~~~~~~~~~~~

  You can mark the path "aws-amplify" as external to exclude it from the bundle, which will remove this error.


✘ [ERROR] Could not resolve "@react-native-async-storage/async-storage"

    ../node_modules/thirdweb/dist/esm/wallets/in-app/native/helpers/storage/local.js:1:25:
      1 │ import AsyncStorage from "@react-native-async-storage/async-storage";
        ╵                          ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  You can mark the path "@react-native-async-storage/async-storage" as external to exclude it from the bundle, which will remove this error.


✘ [ERROR] Could not resolve "shamir-secret-sharing"

    ../node_modules/thirdweb/dist/esm/wallets/in-app/native/helpers/wallet/creation.js:2:22:
      2 │ import { split } from "shamir-secret-sharing";
        ╵                       ~~~~~~~~~~~~~~~~~~~~~~~

  You can mark the path "shamir-secret-sharing" as external to exclude it from the bundle, which will remove this error.


✘ [ERROR] Could not resolve "react-native-aes-gcm-crypto"

    ../node_modules/thirdweb/dist/esm/wallets/in-app/native/helpers/wallet/encryption.js:1:25:
      1 │ import AesGcmCrypto from "react-native-aes-gcm-crypto";
        ╵                          ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  You can mark the path "react-native-aes-gcm-crypto" as external to exclude it from the bundle, which will remove this error.


✘ [ERROR] Could not resolve "react-native-quick-crypto"

    ../node_modules/thirdweb/dist/esm/wallets/in-app/native/helpers/wallet/encryption.js:2:24:
      2 │ import QuickCrypto from "react-native-quick-crypto";
        ╵                         ~~~~~~~~~~~~~~~~~~~~~~~~~~~

  You can mark the path "react-native-quick-crypto" as external to exclude it from the bundle, which will remove this error.


✘ [ERROR] Could not resolve "@aws-sdk/client-lambda"

    ../node_modules/thirdweb/dist/esm/wallets/in-app/native/helpers/wallet/recoveryCode.js:1:44:
      1 │ import { InvokeCommand, LambdaClient } from "@aws-sdk/client-lambda";
        ╵                                             ~~~~~~~~~~~~~~~~~~~~~~~~

  You can mark the path "@aws-sdk/client-lambda" as external to exclude it from the bundle, which will remove this error.


✘ [ERROR] Could not resolve "@aws-sdk/credential-providers"

    ../node_modules/thirdweb/dist/esm/wallets/in-app/native/helpers/wallet/recoveryCode.js:2:40:
      2 │ ...t { fromCognitoIdentityPool } from "@aws-sdk/credential-providers";
        ╵                                       ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  You can mark the path "@aws-sdk/credential-providers" as external to exclude it from the bundle, which will remove this error.


✘ [ERROR] Could not resolve "shamir-secret-sharing"

    ../node_modules/thirdweb/dist/esm/wallets/in-app/native/helpers/wallet/retrieval.js:1:24:
      1 │ import { combine } from "shamir-secret-sharing";
        ╵                         ~~~~~~~~~~~~~~~~~~~~~~~

  You can mark the path "shamir-secret-sharing" as external to exclude it from the bundle, which will remove this error.


✘ [ERROR] Could not resolve "@react-native-async-storage/async-storage"

    ../node_modules/thirdweb/dist/esm/wallets/storage/nativeStorage.js:1:25:
      1 │ import AsyncStorage from "@react-native-async-storage/async-storage";
        ╵                          ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  You can mark the path "@react-native-async-storage/async-storage" as external to exclude it from the bundle, which will remove this error.


✘ [ERROR] Could not resolve "react-native"

    ../node_modules/thirdweb/dist/esm/wallets/wallet-connect/controller.js:44:40:
      44 │             const { Linking } = require("react-native");
         ╵                                         ~~~~~~~~~~~~~~

  You can mark the path "react-native" as external to exclude it from the bundle, which will remove this error. You can also surround this "require" call with a try/catch block to handle this failure at run-time instead of bundle-time.


✘ [ERROR] Build failed with 14 errors:

  ../node_modules/thirdweb/dist/esm/wallets/coinbase/coinbaseMobileSDK.js:1:26: ERROR: Could not
  resolve "@coinbase/wallet-mobile-sdk"
  ../node_modules/thirdweb/dist/esm/wallets/coinbase/coinbaseMobileSDK.js:10:4: ERROR: Could not
  resolve "@coinbase/wallet-mobile-sdk/build/WalletMobileSDKEVMProvider"
  ../node_modules/thirdweb/dist/esm/wallets/in-app/native/auth.js:1:21: ERROR: Could not resolve
  "aws-amplify"
  ../node_modules/thirdweb/dist/esm/wallets/in-app/native/auth.js:2:28: ERROR: Could not resolve
  "expo-web-browser"
  ../node_modules/thirdweb/dist/esm/wallets/in-app/native/helpers/auth/cognitoAuth.js:1:30: ERROR:
  Could not resolve "aws-amplify"
  ...
```

</details>


<details>

# Welcome to Remix + Cloudflare!

- 📖 [Remix docs](https://remix.run/docs)
- 📖 [Remix Cloudflare docs](https://remix.run/guides/vite#cloudflare)

## Development

Run the dev server:

```sh
npm run dev
```

To run Wrangler:

```sh
npm run build
npm run start
```

## Typegen

Generate types for your Cloudflare bindings in `wrangler.toml`:

```sh
npm run typegen
```

You will need to rerun typegen whenever you make changes to `wrangler.toml`.

## Deployment

> [!WARNING]
> Cloudflare does _not_ use `wrangler.toml` to configure deployment bindings.
> You **MUST** [configure deployment bindings manually in the Cloudflare dashboard][bindings].

First, build your app for production:

```sh
npm run build
```

Then, deploy your app to Cloudflare Pages:

```sh
npm run deploy
```

[bindings]: https://developers.cloudflare.com/pages/functions/bindings/

</details>
