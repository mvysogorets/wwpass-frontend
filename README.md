# wwpass-frontend

WWPass authentication and client-side encryption library.

## Install

To install library dependencies, run:

```shell
npm install
```

To build a standalone library version, run:

```shell
npm run build
```

## Usage

To initialize WWPass QR-code authentication use:

(NPM module, import with namespace)
```js
import * as WWPass from 'wwpass-frontend';

WWPass.authInit({
  qrcode: document.querySelector('#qrcode-container'),
  ticketURL: `${urlBase}getticket.php`,
  callbackURL: `${urlBase}login.php`,
});
```

(NPM module, cherry-pick)
```js
import { authInit }  from 'wwpass-frontend';

authInit({
  qrcode: document.querySelector('#qrcode-container'),
  ticketURL: `${urlBase}getticket.php`,
  callbackURL: `${urlBase}login.php`,
});
```

(Standalone script)
```html
<script src="wwpass-frontend.js"></script>
<script>
WWPass.authInit({
  qrcode: document.querySelector('#qrcode'),
  passkey: document.querySelector('#button--login'),
  ticketURL: `${urlBase}getticket.php`,
  callbackURL: `${urlBase}login.php`,
});
</script>
```

## authInit options
 - `qrcode`: DOM element or query selector for authentication QRCode
 - `passkey`: *OPTIONAL* DOM element or query selector that holds button for hardware PassKey authentication. If the element is empty, default "Authenticate with PassKey" button will be rendered.
 - `ticketURL`: URL to request WWPass ticket for authentication. On request to this URL the server should get new ticket via WWPass server API and return json object with ticket and it's ttl in seconds ex.: `{"ticket": "WWPass%20Developers:81f7ba34f27e9707787fd73d43463a3d4b9a0603@p-sp-02-20:16033", "ttl": 600}`
 - `callbackURL`: after successful WWPass authentication the user will be redirected to this URL. Following parameters will be appended to the URL:
    - `wwp_version`: current version of the protocol. For this library it's always `2`
    - `wwp_ticket`: ticket used for authentication
    - `wwp_status` and `wwp_reason`: always `200`, `"OK"` for successful authentications
 - `ppx`: *OPTIONAL* Alternative prefix for `callbackURL` parameters. Defaults to `wwp_`

## Support

If you have any questions, contact us support@wwpass.com.

## License

MIT © WWPass Corporation