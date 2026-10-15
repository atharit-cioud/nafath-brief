Version: NAFATH-V2 
Track:Networking 

Overview
NAFATH-V2 | Discovery Mission
When an emergency happens, responders need their communication systems to work, even if the network is busy or something goes wrong. Keeping a 5G emergency service reliable is not just a networking task. Software teams need to make sure failed requests can be retried without creating duplicate reports. AI can help predict when traffic is likely to increase, while mobile apps should let responders keep working when they lose signal. Network slicing can give emergency traffic different service settings, but it still depends on the underlying infrastructure. Cybersecurity teams need to detect attacks and restore affected services quickly. Finally, well-organized data helps teams understand usage patterns and make better decisions. Together, these areas make the service more dependable, although no single solution can prevent every outage

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

Cybersecurity

Data

Misconception in My Track

Open Questio
