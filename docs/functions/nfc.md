# NFC

**NFC functionality is currently in trial.**

From version 6.0.0 onwards of the app, an NFC tag can be used to add a diary entry to the app.
The NFC tag should have the same data as a QR code, in the following format:

| Record 0 - Link                                | Record 1 - External          |
| ---------------------------------------------- | ---------------------------- |
| https://tracing.covid19.govt.nz/scan#data=...  | nz.govt.health.covidtracer   |

*NB - Data payload should be the same as a QR scan, e.g. `NZCOVIDTRACER:eyJ0eXAiOiJlbnRyeSIsImdsbiI6IlRlc3QiLCJvcG4iOiJUZXN0IiwiYWRyIjoiVGVzdCIsInZlciI6ImMxOToxIn0=`

The device will need to:
- Have hardware capability for NFC
- Have background NFC scanning enabled on the operating system
- [iPhones need to be XS or newer to have background NFC scanning](https://developer.apple.com/documentation/corenfc/adding_support_for_background_tag_reading)
- Have version 6.0.0 or newer of NZ COVID Tracer installed
- Be unlocked
- Be held close to the tag

This will open, or prompt opening, NZ COVID Tracer with a confirmation that the diary entry was successfully added.
