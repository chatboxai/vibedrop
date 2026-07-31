# @vibedrop/sdk

HTTP client SDK for the VibeDrop API.

```ts
import { VibedropClient, loadConfig, packDir } from "@vibedrop/sdk";

const cfg = await loadConfig();
const client = new VibedropClient(cfg);

if (!cfg.apiKey) {
  cfg.apiKey = await client.createAnonKey();
}

const zip = await packDir("./dist");
const { site, claimUrl } = await client.deploy(zip, {
  visibility: "unlisted", // or "public" for moderated Explore discovery
});
console.log(site.url); // https://abc123.vibedrop.site
console.log(claimUrl); // one-time account claim URL, or null
```

`client.update()` manages `visibility`, Pro password protection, visitor
messages, optional branding, and the site title.

See [vibedrop.cc](https://vibedrop.cc) for details.
