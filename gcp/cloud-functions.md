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
- 'Container to production in seconds'
- Built on top of open standard - **knative**
- Fully managed serverless platform for **containerized** applications 
- Fully integrated end-to-end developer experience
  - No limitations on languages, binaries & dependencies
  - Easily portable because of container based architecture

> Cloud Run for Anthos
- Anthos: Run kubernetes clusters anywhere. i.e cloud, multi cloud & on-premise
- Deploy your workloads to anthos clusters running either on premise or google cloud

# Cloud Functions - 2nd generation
- It uses 'cloud run services & revisions' internally for serverless execution which was not possible in 1st gen
- **Longer Request Timeout**: upto 60 mins [1st gen has only 9mins]
- **Large Instances Size**: upto 16GB ram and 4vCPU [1st has max 8GB ram & 2 vCPU]
- **Concurrency**: upto 1000 concurrent requests per function instance [v1: only 1 request per instance]
- **Multiple Function Revisions** and **Traffic Splitting** supported [v1 not supported]
- Support **90+** event types - enabled by Eventarc [v1 has only **7** event types]
