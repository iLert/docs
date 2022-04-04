---
description: >-
  Two improve your account's security, iLert suggests that you setup two-factor
  authentication for it. We especially encourage Account owners or Admins to use
  MFA.
---

# 🔐 Two-factor authentication / MFA

iLert supports two-factor authentication setups for every user account, unrelated to the purchased subscription plan. You may activate multiple 2FA methods e.g. authenticator app as backup for your U2F device.

## Two-factor methods

### Code generation apps

Most used / common authenticator apps:

| App name                | Apple Appstore                                                            | Google Playstore                                                                                           |
| ----------------------- | ------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Google Authenticator    | [Link](https://apps.apple.com/de/app/google-authenticator/id388497605)    | [Link](https://play.google.com/store/apps/details?id=com.google.android.apps.authenticator2\&hl=de\&gl=US) |
| Duo Mobile              | [Link](https://apps.apple.com/de/app/duo-mobile/id422663827)              | [Link](https://play.google.com/store/apps/details?id=com.duosecurity.duomobile\&hl=de\&gl=US)              |
| Authy                   | [Link](https://apps.apple.com/de/app/twilio-authy/id494168017)            | [Link](https://play.google.com/store/apps/details?id=com.authy.authy\&hl=de\&gl=US)                        |
| Microsoft Authenticator | [Link](https://apps.apple.com/de/app/microsoft-authenticator/id983156458) | [Link](https://play.google.com/store/apps/details?id=com.azure.authenticator\&hl=de\&gl=US)                |

### FaceID, TouchID, Apple Watch or other device authentication

Even if you are not in posession of a hardware token like a Yubico Security Key, you may choose the option "Use security key" with supporting Apple or Microsoft devices that offer biometrical authentication sensors e.g. TouchID or double-tap on Apple Watch. Do not forget that you have to register and validate again, meaning **you will be asked to verify twice during the setup** of this 2FA option.

### Hardware tokens / FIDO (U2F) Keys

If available you may select "**Use security key**" option with your U2F / [WebAuthn](https://www.w3.org/TR/webauthn-2/) supporting devices such as Yubico Security Keys. Do not forget that you have to register and validate again, meaning **you will be asked to verify twice during setup** of this 2FA option.

## FAQ

### I lost my authenticator app / TOPT generator / device how can I access my account?

If you have lost your app or device you may use your recovery-codes, handed out during initial setup of your 2FA to get access to the account. **Note**: you were handed out 5 recovery codes only and each becomes burnt when it is used. So it is highly adviced to immediately use the recovery codes to access and remove 2FA from your account (requires at least 2 recovery codes). Once removed you may setup 2FA again using a new device / app.

In case you were using a FIDO device or you have lost / burnt your recovery codes you will need to contact [iLert support](../contact.md#support) providing additional details of verification e.g. passport to have 2FA reset from your account.
