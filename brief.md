Version: NAFATH-V2 
Track:Networking 

Overview
NAFATH-V2 | Discovery Mission
When an emergency happens, responders need their communication systems to work, even if the network is busy or something goes wrong. Keeping a 5G emergency service reliable is not just a networking task. Software teams need to make sure failed requests can be retried without creating duplicate reports. AI can help predict when traffic is likely to increase, while mobile apps should let responders keep working when they lose signal. Network slicing can give emergency traffic different service settings, but it still depends on the underlying infrastructure. Cybersecurity teams need to detect attacks and restore affected services quickly. Finally, well-organized data helps teams understand usage patterns and make better decisions. Together, these areas make the service more dependable, although no single solution can prevent every outage 
However, a key challenge remains in handling conflicting updates when multiple responders edit the same incident offline and reconnect simultaneously.

Software
GET is a safe HTTP method because it does not ask the server to change data. An idempotent method has the same intended effect even when the same request is sent more than once; PUT and DELETE are examples. This matters when an emergency app loses its connection and retries a request. If it repeats a normal POST, the server might create the same incident twice. Idempotency keys can help prevent that when the API supports them.
Resource: RFC 9110, Sections 9.2.1–9.2.2 — https://www.rfc-editor.org/rfc/rfc9110.html#section-9.2.2

AI
Overfitting happens when an AI model becomes too focused on its training data and struggles with new situations. Imagine a model that predicts 5G congestion accurately during normal days but performs badly during an emergency. Cross-validation helps us check whether the model works on data it has not trained on. Because network traffic changes over time, it is better to test using earlier periods for training and later periods for validation, rather than mixing past and future observations.
Resource: Scikit-learn User Guide, Cross-validation — https://scikit-learn.org/stable/modules/cross_validation.html

Mobile
An emergency responder should still be able to use the app when the network goes down. The app could keep important information on the device and save new reports locally until a connection is available. Once the signal returns, it should upload the pending changes securely. It also needs a way to avoid duplicate submissions and handle conflicting updates. Clear messages such as ‘Saved offline’ and ‘Synced’ would help responders know whether their information has reached the server.
Resource: Android Developers, Build an offline-first app — https://developer.android.com/topic/architecture/data-layer/offline-first

Networking

Network slicing allows a 5G operator to create different logical networks on shared equipment. An emergency service could have a slice with settings designed for its traffic, helping it perform better when many people are using the network. However, slicing does not mean the service can never fail. A power outage or a problem in shared infrastructure may still affect it. For that reason, the operator also needs backup systems, monitoring, capacity planning, and regular tests.
Resource: 3GPP, Network Slicing overview — https://www.3gpp.org/technologies/slicing

Cybersecurity
If an emergency 5G service is attacked, the team needs to respond in an organized way. It should first recognize and investigate the suspicious activity, then take steps to limit the damage. After that, the team can restore affected systems and check that the service is working properly. What happened should also be reviewed so the same problem is less likely to happen again. NIST's current guidance connects these activities with preparation and wider cybersecurity risk management.
Resource: NIST SP 800-61 Rev. 3 — https://csrc.nist.gov/pubs/sp/800/61/r3/final

Data
A star schema puts measurements, such as daily network usage, in a central fact table linked to dimension tables for dates, regions, and services. A snowflake schema splits some of those dimensions into smaller related tables. This reduces repetition but makes queries more complicated. For a dashboard showing daily 5G usage by region, I would start with a star schema because it is simpler to understand and usually easier to report from. The best choice still depends on the data requirements.
Resource: Microsoft Learn, Star schema guidance — https://learn.microsoft.com/en-us/power-bi/guidance/star-schema/

Misconception in My Track
At first, it is easy to assume that an idempotent HTTP request must return exactly the same response every time. That is not what idempotent means. The important point is that repeating the request has the same intended effect on the server. For example, the first DELETE request might remove a record successfully, while the next one could say the record was not found. In both cases, the record is gone. I also learned that POST requests are not automatically safe to retry, but an API can add an idempotency-key mechanism to help prevent duplicate operations. This is especially useful when a mobile connection drops before the app receives confirmation.
Resource: RFC 9110, Section 9.2.2 — https://www.rfc-editor.org/rfc/rfc9110.html#section-9.2.2

Open Questio
If two emergency responders update the same incident while offline, how should the system decide which changes to keep when both devices reconnect?
