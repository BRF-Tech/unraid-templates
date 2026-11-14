# BRF Tech - Unraid templates

Unraid Community Applications templates for the open-source software made by
[BRF Tech](https://github.com/BRF-Tech).

| App | Template | Image | Project |
|---|---|---|---|
| filex - self-hosted web file manager | [`templates/filex.xml`](templates/filex.xml) | `ghcr.io/brf-tech/filex` (amd64, arm64) | [BRF-Tech/filex](https://github.com/BRF-Tech/filex) |

## Install

Search for the app in **Apps** (Community Applications) on your Unraid server.

To add a template by hand, save its XML file to
`/boot/config/plugins/dockerMan/templates-user/` on the flash drive, then open
**Docker > Add Container** and pick it from the **Template** list.

## filex

| Setting | Required | Notes |
|---|---|---|
| Files (`/srv/files`) | yes | The share filex manages, for example `/mnt/user/files`. It becomes the first storage on the first start. |
| Public URL (`FILEX_PUBLIC_URL`) | yes | The address you open filex at, for example `http://192.168.1.10:5212`. Share links and sign-in redirects are built from it. |
| Data (`/data`) | yes | `/mnt/user/appdata/filex`: database, search index, thumbnails. |
| Admin Email / Admin Password | no | Empty: the administrator `admin@local` is created with a random password, printed once in the container log and saved to `/mnt/user/appdata/filex/.first-run.txt`. |
| Secret Key (`FILEX_SECRET_KEY`) | no | 32 or more random characters. Needed for S3 access keys, push notifications and sign-in provider secrets saved in the admin panel. Back it up and keep it unchanged. |
| PUID / PGID | no | `99` / `100` (nobody / users), so files filex writes to your shares get the usual Unraid owner. Empty: runs as root. |

The administrator signs in at `http://<server>:5212/admin`; accounts you create
for other people sign in at `/drive`.

The template uses the `latest` tag, which follows the newest filex release, so
Unraid shows an update when a new version is published. To stay on one version,
put a release tag in **Repository**, for example `ghcr.io/brf-tech/filex:v0.60.2`
([releases](https://github.com/BRF-Tech/filex/releases)).

Documentation: <https://docs.filex.sh>

## Support

- Problems with filex itself: <https://github.com/BRF-Tech/filex/issues>
- Problems with a template in this repository: <https://github.com/BRF-Tech/unraid-templates/issues>

## License

The templates and files in this repository are MIT licensed, see [LICENSE](LICENSE).
filex is MIT licensed as well.
