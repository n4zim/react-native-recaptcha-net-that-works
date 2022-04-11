# reCAPTCHA.net for React Native (Android and iOS)

[![License MIT](https://img.shields.io/badge/licence-MIT-blue.svg)](https://github.com/n4zim/react-native-recaptcha-net-that-works/blob/master/LICENSE)
[![npm version](https://img.shields.io/npm/v/react-native-recaptcha-net-that-works.svg)](https://www.npmjs.com/package/react-native-recaptcha-net-that-works)
[![npm downloads](https://img.shields.io/npm/dt/react-native-recaptcha-net-that-works.svg)](#install)

A reCAPTCHA.net library for React Native (Android and iOS) that works.

| Normal | Invisible |
| - | - |
| <img src='https://raw.githubusercontent.com/n4zim/react-native-recaptcha-net-that-works/master/screenshots/normal.gif' width='240' /> | <img src='https://raw.githubusercontent.com/n4zim/react-native-recaptcha-net-that-works/master/screenshots/invisible.gif' width='240' /> |

_Looking for [React DOM version](https://github.com/douglasjunior/react-recaptcha-that-works)?_

## Install

### Install the module

```bash
  yarn add react-native-recaptcha-net-that-works react-native-webview
```
Or
```bash
  npm i -S react-native-recaptcha-net-that-works react-native-webview
```

_See the [`react-native-webview` Getting Started Guide](https://github.com/react-native-community/react-native-webview/blob/master/docs/Getting-Started.md)._

## Usage

With <strong>JavaScript</strong>:

```jsx
import React, { useRef } from 'react';
import { View, Button } from 'react-native';

import Recaptcha from 'react-native-recaptcha-net-that-works';

const App = () => {
    const recaptcha = useRef();

    const send = () => {
        console.log('send!');
        this.recaptcha.current.open();
    }

    const onVerify = token => {
        console.log('success!', token);
    }

    const onExpire = () => {
        console.warn('expired!');
    }

    return (
        <View>
            <Recaptcha
                ref={recaptcha}
                siteKey="<your-recaptcha-public-key>"
                baseUrl="http://my.domain.com"
                onVerify={onVerify}
                onExpire={onExpire}
                size="invisible"
            />
            <Button title="Send" onPress={send} />
        </View>
    );
}
```

<details>
    <summary>Or with <strong>TypeScript</strong>:</summary>

```tsx
import React, { useRef } from 'react';
import { View, Button } from 'react-native';

import Recaptcha, { RecaptchaHandles } from "react-native-recaptcha-net-that-works";

// ...

export const Component: React.FC = () => {
    const recaptcha = useRef<RecaptchaHandles>();

    const send = () => {
        console.log('send!');
        recaptcha.current?.open();
    };

    const onVerify = (token: string) => {
        console.log('success!', token);
    };

    const onExpire = () => {
        console.warn('expired!');
    }

    return (
        <View>
            <Recaptcha
                ref={recaptcha}
                siteKey="<your-recaptcha-public-key>"
                baseUrl="http://my.domain.com"
                onVerify={onVerify}
                onExpire={onExpire}
                size="invisible"
            />
            <Button title="Send" onPress={send} />
        </View>
    );
};
```
</details>

<br />

For more details, see the [Sample Project](https://github.com/n4zim/react-native-recaptcha-net-that-works/blob/master/Sample/src/App.js) or try the [Online demo](https://snack.expo.dev/@douglasjunior/react-native-recaptcha-that-works).

## Props

|Name|Value|Default|Description|
|-|-|-|-|
|headerComponent|`React Element`||A component to render on top of Modal.|
|footerComponent|`React Element`||A component to render on bottom of Modal.|
|loadingComponent|`React Element`||A custom loading component.|
|style|[`ViewStyle`](https://reactnative.dev/docs/view-style-props)||Customize default style such as background color.|
|modalProps|[ModalProps](https://reactnative.dev/docs/modal)||Override the Modal props.|
|webViewProps|[WebViewProps](https://github.com/react-native-webview/react-native-webview/blob/master/docs/Reference.md)||Override the WebView props.|
|lang|`string`||[Language code](https://developers.google.net/recaptcha/docs/language).|
|siteKey|`string`||(Required) Your sitekey.|
|baseUrl|`string`||(Required) The URL (domain) configured in the reCAPTCHA setup. (ex. http://my.domain.com)|
|size|`'invisible'`, `'normal'` or `'compact'`|`'normal'`|The size of the widget.|
|theme|`'dark'` or `'light'`|`'light'`|The color theme of the widget.|
|onLoad|`function()`||A callback function, executed when the reCAPTCHA is ready to use.|
|onVerify|`function(token)`||(Required) A callback function, executed when the user submits a successful response. The reCAPTCHA response token is passed to your callback.|
|onExpire|`function()`||A callback function, executed when the reCAPTCHA response expires and the user needs to re-verify.|
|onError|`function(error)`||A callback function, executed when reCAPTCHA encounters an error (usually network connectivity) and cannot continue until connectivity is restored. If you specify a function here, you are responsible for informing the user that they should retry.|
|onClose|`function()`|| A callback function, executed when the Modal is closed.|
|enterprise|`boolean`|`false`| (Experimental) Use the new [reCAPTCHA Enterprise API](https://cloud.google.net/recaptcha-enterprise/docs/using-features).|

Note: If `lang` is not set, then device language is used.

## Methods

|Name|Type|Description|
|-|-|-|
|open|`function`|Open the reCAPTCHA Modal.|
|close|`function`|Close the reCAPTCHA Modal.|

Note: If using `size="invisible"`, then challenge run automatically when `open` is called.

## reCAPTCHA v2 docs

- [I'm not a robot](https://developers.google.net/recaptcha/docs/display)
- [Invisible](https://developers.google.net/recaptcha/docs/invisible)

## reCAPTCHA Enterprise docs

- [Overview](https://cloud.google.net/recaptcha-enterprise/docs/)
- [Using features](https://cloud.google.net/recaptcha-enterprise/docs/using-features)

## Contribute

New features, bug fixes and improvements are welcome! For questions and suggestions, use the [issues](https://github.com/n4zim/react-native-recaptcha-net-that-works/issues).

<a href="https://www.patreon.com/douglasjunior"><img src="http://i.imgur.com/xEO164Z.png" alt="Become a Patron!" width="200" /></a>
[![Donate](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=E32BUP77SVBA2)

## License

```
The MIT License (MIT)

Copyright (c) 2020 Douglas Nassif Roma Junior
```

See the full [license file](https://github.com/n4zim/react-native-recaptcha-net-that-works/blob/master/LICENSE).
