![](mainSequence.png)


<!--
@startuml mainSequence

User -> Browser: Submit
Browser -> WebApp: POST(Service=TechAnalysis, Instrument, TimeFrame)
WebApp -> API: /tec-analysis/Instrument, TimeFrame
API -> Storage: get_prompt(service: tech-analysis)
API <-- Storage: prompt
API -> DataStream: get-data(instrument, time-frame)
API <-- DataStream: data
API -> API: build_prompt
API -> OpenAI: create-text(prompt)
API <-- OpenAI: message
WebApp <--API: Response(tech-analysis-response)
Browser <-- WebApp: Response(tech-analysis)

@enduml
-->


## API Messages

### Tech Analysis

![](RequestMessage.png)

<!--
@startjson RequestMessage
{
   "user": "james-t-kirk",
   "service":"tech-analysis",
   "instrument":"EUR/USD",
   "time-frame": "H1",
   "request-datetime": "2024-04-01 05:00:00" 
}
@endjson
-->

<!--
@startjson ResponseMessage
{
   "user": "james-t-kirk",
   "service":"tech-analysis",
   "instrument":"EUR/USD",
   "time-frame": "H1",
   "message": "The EUR/USD will go long",
   "request-datetime": "2024-04-01 05:00:00",
   "response-datetime":  "2024-04-01 05:00:01"
}
@endjson
-->


![](ResponseMessage.png)