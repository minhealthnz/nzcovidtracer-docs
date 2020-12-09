# NZ COVID Tracer

In the context of the New Zealand COVID-19 pandemic response the primary objective 
of the solution is to support contact tracing, by providing tools for consumers to
complete the following objectives:

 - Provide up-to-date contact details, so contact tracers can get in contact faster 
   when tracing close contacts of people who have tested positive to COVID-19.
 - Keep a ‘digital diary’ of where they have been and who they have seen, so if they 
   test positive for COVID-19 they can accurately recall their movements to contact 
   tracers.
 - Receive an alert if they have been in the same place around the same time as 
   someone who later tests positive for COVID-19.
 - Record their NHI to speed up identification and processing when presenting for a 
   test a community-based assessment centre. 
 - Allow a user to enable Bluetooth-based Exposure Notifications on their compatible
   iOS or Android smartphone

It is noted that this solution is just one of several technologies and tools that 
contribute to contact tracing in New Zealand, and it is not intended to be a 
'silver bullet'. 

## Documentation


### Architecture
Information about the technical solution architecture is in `architecture/`
- [Overview](architecture/overview.md): A high level overview of the entire 
  solution
- [AWS Infrastructure](architecture/aws-infrastructure.md): The deployment 
  view of components in AWS

### Functionality
Each of the key functions outlined above are explained in further detail in 
the `functions/` directory.
- [Authentication](functions/authentication.md): Logging in and authentication
- [Personal Details](functions/personal-details.md): Sharing contact details 
  with the contact tracing team
- [Digital Diary](functions/digital-diary.md): Using the digital diary to 
  record visits, and privacy of diary entries
- [Contact Alerts](functions/contact-alerts.md): Receiving contact alerts 
  for potential exposure to COVID-19 at checked-in locations
- [Record NHI](functions/record-nhi.md): Recording NHI for faster tests
- [Exposure Notifications](functions/apple-google-exposure-notifications.md):
  Enabling Google/Apple Exposure Notifications using Bluetooth

## Google/Apple Exposure Notifications
More details about the GAEN framework is detailed in `exposure-notifications/`
- [Scoring](exposure-notifications/scoring.md): Details about the risk scoring
  alogrithm implementation based on COVID Green
- [In-App Screens](exposure-notifications/in-app-flows.md): Visuals of the in-
  app screens for exposure notifications.


## Other links
Links to other published resources related to NZ COVID Tracer
- [Health website][1]: The main information website for the app
- [Privacy & Security][2]: Details about the privacy and security controls, 
  including links to the latest Privacy Impact Assessment
- [COVID Green][3]: The open source project implementation the Exposure 
  Notifications functionality is based off

[1]: https://health.govt.nz/nz-covid-tracer
[2]: https://www.health.govt.nz/our-work/diseases-and-conditions/covid-19-novel-coronavirus/covid-19-resources-and-tools/nz-covid-tracer-app/privacy-and-security-nz-covid-tracer
[3]: https://github.com/covidgreen
