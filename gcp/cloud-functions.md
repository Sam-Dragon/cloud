# Cloud Functions

- It is FAAS or serverless 
- It is mainly used for run code based on events.
  - Events can be triggerd from cloud storage, cloud pub/sub, HTTP calls, firebase, cloud firestore, stack driver   logging
- Dont care about Infrastructure
- Short lived process
- It is pay for usage which includes cpu, memory, no. of invocations,   computation time of invocations
- It is time-bounded [Max valid till 60 mins] 
- It has two generations of product version
  
> Concepts
- Events: upload object to cloud storage
- Trigger: decides function to trigger based on event
  
# Cloud Run
- It is CAAS or serverless 
- It belongs to 2 gen of cloud function
- 'Container to production in seconds'
- Built on top of open standard - **knative**
- Fully managed serverless platform for **containerized** applications 
- Fully integrated end-to-end developer experience
  - No limitations on languages, binaries & dependencies
  - Easily portable because of container based architecture

> Cloud Run for Anthos
- Anthos: Run kubernetes clusters anywhere. i.e cloud, multi cloud & on-premise
- Deploy your workloads to anthos clusters running either on premise or google cloud
