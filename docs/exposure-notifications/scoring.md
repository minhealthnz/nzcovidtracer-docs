# NZ COVID Tracer - GAEN Notification Algorithm

NZ COVID Tracer uses the COVID Green React Native Exposure Notification Service 
[plugin][1] to interface with the EN framework on the device.

This plugin implements a risk scoring algorithm using the scoring method found 
in iOS v1 and Android v1.5 of the EN framework.

NZ COVID Tracer does not currently use the new "Exposure Windows" (iOS v2, 
Android v1.6) verison of the EN framework.

![COVID Green Risk Scoring](../assets/en-scoring-explainer.png)

In summary:

- Devices record interactions with other nearby EN-activated devices, including
  attenuation, duration, and other metadata (transmit power, etc). These 
  'exposures' are shown as the coloured dots. 

- When the device downloads Diagnosis Keys (keys from a positive case) it 
  re-calculates the Rolling Proximity Identifiers from those Diagnosis Keys
  and checks if there are any matching identifiers in the record on the device.

- If matching exposures are found they are fed into the risk scoring
  calculation as follows:
    - Sort each exposure into one of three buckets, _immediate_, _near_, and 
      _medium_, based on the configured `durationAtAttenuationThresholds`.
    - For each bucket, sum the number of minutes of exposures within that 
      bucket
    - Weight each bucket using the corresponding `thresholdWeightings` value
    - Sum the weighted value to give a total weighted exposure minutes.

- This calculation gives a risk score as "exposure minutes", i.e. the number of 
  cumulative minutes this device has spent in proximity to other devices linked
  to a confirmed positive case of COVID-19.

- If this score is above a given threshold, the user is alerted through a push
  notification and in-app message alerting them to appropriate next steps.


[1]: https://github.com/covidgreen/react-native-exposure-notification-service
[2]: https://developer.apple.com/documentation/exposurenotification/enexposureconfiguration/3583692-minimumriskscore
[3]: https://developer.apple.com/documentation/exposurenotification/enexposureconfiguration/3586319-attenuationlevelvalues
[4]: https://developer.apple.com/documentation/exposurenotification/enexposureconfiguration/3583687-attenuationweight
[5]: https://developer.apple.com/documentation/exposurenotification/enexposureconfiguration/3586320-dayssincelastexposurelevelvalues
[6]: https://developer.apple.com/documentation/exposurenotification/enexposureconfiguration/3583689-dayssincelastexposureweight
[7]: https://developer.apple.com/documentation/exposurenotification/enexposureconfiguration/3586321-durationlevelvalues
[8]: https://developer.apple.com/documentation/exposurenotification/enexposureconfiguration/3583691-durationweight
[9]: https://developer.apple.com/documentation/exposurenotification/enexposureconfiguration/3586323-transmissionrisklevelvalues
[10]: https://developer.apple.com/documentation/exposurenotification/enexposureconfiguration/3583694-transmissionriskweight