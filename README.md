# Open Tracked Data Store Lookup

_Server variable template for Google Tag Manager (server container)._

Reads one thing your Open Tracked Data Store remembers about the visitor: hashed email, hashed phone, hashed first or last name, external ID, or the Meta click and browser IDs. Use it with the **Open Tracked Data Store Save** tag. If the event already carries the value, that value is returned and the Data Store is not asked.

## How to use

1. Add this variable to your server container with the Data Store address and token from your Open Tracked dashboard.
2. Set **Field to read** (`em`, `ph`, `fn`, `ln`, `external_id`, `fbc` or `fbp`) and, optionally, the event data key whose own value should win.
3. Use the variable in an **Augment event** transformation or directly in a tag.

## Fields

| Field | Name | What it does |
|---|---|---|
| Data Store address | `apiUrl` | From the Data Store power-up in your Open Tracked dashboard, for example https://app.opentracked.io/api/ds/v1/123. |
| Data Store token | `token` | From the same page. |
| Find the visitor by | `keySource` |  |
| Field to read | `field` | em, ph, fn, ln, external_id, fbc or fbp. |
| Use the event's own value first (optional) | `eventDataKey` | An event data key such as x-fb-ud-em. When the event has it, that value is returned and the Data Store is not asked. |
| Remember an answer for (seconds) | `cacheSeconds` | Several fields of one visitor share one answer. |

## Privacy

- The visitor is looked up by a SHA-256 hash of the GA4 client ID or user ID, never by the ID itself.
- Only hashed personal data is ever read back.
- One answer is kept for a few seconds (default 30) in the template storage of the server instance, so several fields of one visitor share one request. If the Data Store does not answer within two seconds the variable returns nothing and your tags run as before.

## Permissions

- **Reads event data**: Reads the client ID or user ID and the optional event value.
- **Sends HTTP requests**: Only to `https://app.opentracked.io/api/ds/` and `https://app.openserver.digital/api/ds/`.
- **Accesses template storage**: Keeps the short-lived answer described above.

## Notes

Requires an Open Tracked account. The Data Store must be switched on.

## About Open Tracked

[Open Tracked](https://opentracked.io) is a first-party tracking service: a tagging server on your own domain, an analytics pixel and a CRM. Documentation: https://docs.opentracked.io/google-tag-manager

## License

Apache License 2.0, see [LICENSE](LICENSE).
