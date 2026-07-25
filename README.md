# amp-templates

Custom [AMP](https://cubecoders.com/amp) (CubeCoders Application Management Panel) Generic Module deployment templates.

## Templates

| Template | App | Notes |
|---|---|---|
| `pst.kvp` | [zaigie/palworld-server-tool](https://github.com/zaigie/palworld-server-tool) | Palworld server admin dashboard. Linux x86_64/aarch64. Requires an existing Palworld dedicated server with RCON + REST API enabled. |

## Usage

Add this repo to AMP's Configuration Repositories (`Configuration → Instance Deployment → Configuration Repositories`) as:

```
Comsicare/amp-templates:main
```

Then click **Fetch Latest**. The template(s) above will appear in the Create Instance app list after AMP's next restart.
