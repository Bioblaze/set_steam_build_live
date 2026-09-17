> **Deprecated.** Promoting a Steam build live now lives in [blazium-cli](https://github.com/blazium-games/blazium-cli): `blazium-cli deploy steam set-live`. This Action is no longer developed.

# 🎮 Set Steam Build Live

A GitHub composite action for safely publishing a Steam build using the `SetAppBuildLive` Steamworks Web API.

> ⚠️ This action is designed for secure CI/CD pipelines and **must not** be used on client-side or exposed workflows. It requires your **Steamworks Web API publisher key**, which should be kept confidential.

---

## 🔧 Inputs

| Name            | Required | Description                                                                 |
|-----------------|----------|-----------------------------------------------------------------------------|
| `steam_api_key` | ✅        | Your Steamworks Web API publisher authentication key                        |
| `app_id`        | ✅        | Steam App ID of your game                                                  |
| `build_id`      | ✅        | The specific Build ID to publish                                           |
| `beta_key`      | ✅        | The branch key, such as `public` for the default release branch            |
| `steam_id`      | ☑️ (if `public`) | The SteamID of the account confirming the release (needed for `public`)   |
| `description`   | ❌        | An optional internal description for this build                            |

---

## ✅ Outputs

| Name           | Description                             |
|----------------|-----------------------------------------|
| `result_code`  | The HTTP response code returned by Steam|

---

## 🚀 Usage

This Action is deprecated. Promote a Steam build with:

```text
blazium-cli deploy steam set-live --build-id ID --beta-key public
```

Set `BLAZIUM_STEAM_API_KEY`, `BLAZIUM_STEAM_APP_ID`, and (for `public`) `BLAZIUM_STEAM_ID`. See [blazium-cli deploy](https://github.com/blazium-games/blazium-cli).

If `beta_key` is `public`, `steam_id` is required and must have **Edit App** and **Publish** permissions in Steamworks. The account will receive a mobile confirmation.

---

## 🔐 Security Note

Always store sensitive data such as `steam_api_key` and `steam_id` in [GitHub Secrets](https://docs.github.com/en/actions/security-guides/encrypted-secrets). Never hardcode them into workflows or source control.

---

## License

This GitHub Action is distributed under the MIT license. See the `LICENSE` file for more details.

---

This action is maintained by Randolph William Aarseth II <randolph@divine.games>. Please reach out for support or contributions.