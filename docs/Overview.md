# [Timing] Principles of External Signal Ingress for DMF Media Workloads


_(c) AMWA 2026, CC Attribution-NoDerivatives 4.0 International (CC BY-ND 4.0)_

The following document summarises the principles agreed to for ingressing external Signals to a DMF Media Workload. It should be read in conjunction with the previous summary document which defines principles and terminology to which this document refers.  
Previous document reference: [https://specs.amwa.tv/in-002/Overview/](https://specs.amwa.tv/in-002/Overview/)

# Principles of External Signal Ingress for DMF Media Workloads:

![][image1]  
**Figure 1: High level external Signal ingress**

* ‘Signal’ is a generic term for any/all external media feeds that have not yet been conformed into the DMF Media Workload  
* ‘Flow’ is a term for a media feed that is usable in the DMF Media Workload  
* All external Signals entering a DMF Media Workload are conformed on ingress  
* Each Signal is ingressed for use within a Media Workload. Future work will be defining the use of ingressed flows by other local Media Workloads running locally that use a common timing domain

![](images/JT-DMF Use Cases - Ingress Conformance.png)  
**Figure 2: Conformance Function**

* The ingress ‘Conformance’ process ensures all DMF flows can be used as ‘aligned’ within the Media Workload  
* The Conformance Function will be more or less onerous depending on the properties of the incoming Signal  
* There are two key properties of an incoming Signal that determine what processing the ingress conformance needs to do:  
  * Frequency provenance  
  * Timestamp provenance (if present)  
* An ingress registry is required to record key incoming Signal attributes  
  * Incoming Signal frequency derivation \- e.g. traceable to global timing reference  
  * Status of Incoming Signal timestamp (if present) \- usability and effective resolution  
  * Offset applied to timestamp on ingress (ns) (and potentially reason for offset)  
  * Listing of other related incoming Signals that have a timing relationship that need to be preserved  
  * Specification for this registry and how it can be queried by Media Functions is a future topic.

![](images/JT-DMF Ingress v7-with-embedded.drawio.png)  
**Figure 3: Example of multi-Signal Ingress**

* As a result of the Ingress Conformance process, Flows have Indexing Time Stamps quantized to the SMPTE grid for the appropriate media type describing desired Flow timing alignment.   
* Wherever possible the ingress conformance process should avoid adding delay by buffering Signals. Desired alignment between Flows at the output of this process are expressed in terms of the relationship between the Flows’ ITS: the Conformance process manipulates these timestamps where adjustments need to be made.  
    
* The Media Workload clock is a software counter of nanosecond resolution driven from a reliable clock reference such as the facility time reference.   
* ITS offsets per Signal are a Media Workload design decision, configured to correct for anomalies and errors in alignment between Signals arriving at the Media Workload ingress boundary, as well as to ensure phase alignment of timestamps to the media unit grid.  
* An ideal Signal arriving at the DMF ingress boundary will be frequency coherent to a global time reference and will have Origin Time Stamps (OTS) phase-aligned with the SMPTE epoch for the media unit rate, propagated from the point of Signal origination. In this case Conformance is a minimal operation: the OTS for each media unit is used directly to populate the corresponding Flow ITS.  
* The Media Workload clock is used to derive ITS for Flows created from Signals without OTS.  
* Signals with OTS may be excluded from alignment according to their OTS if they have been subject to excessive upstream latency compared to other Signals, or by explicit user choice.  These Signals are treated the same way as Signals with no OTS: the ITS is taken from the Media Workload clock instead.  
* If the incoming video Signal frequency provenance is coherent to the DMF Media Workload then a virtual frame sync function is not needed as part of the video ingress function. If it is unknown or known to not be coherent, this would be required.  
* If the incoming audio Signal frequency provenance is coherent to the DMF Media Workload then a sample rate conversion function is not necessary as part of the audio ingress function. If it is unknown or known to not be coherent, this would be required.  
* Video frame sync and audio sample rate conversion functions use the Media Workload clock to form the stream of media units at the correct rate at their output, aligned to the SMPTE media unit grid. This clock is also used to derive ITS for the resulting rate-corrected Flows. 

# 

# Future work may include

(Including those already mentioned in IN-002, repeated for convenience of a single list)

### **Flow exchange between multiple Media Workloads**

The current work started with Ingress on a Media Workload basis and this should be expanded to the exchange of Flows between local Media Workloads

### **Ingress Registry specification**

As mentioned in this document, time information for Signals that have been confirmed are recorded in a registry that needs to be specified in more detail. 

### **Egress timing**

Complimentary to this document, a focus on the egress of Flows from a Media Workload to the external linear world.

### **Upstream Signal Chain Timing**

For a fully end-to-end solution, timing relationships are better to be captured at the point of acquisition, such as the camera shutter or microphone capsule. Few protocols currently allow this information to be propagated accurately, so additional work outside JT-DMF will be required.

### **Multi-Cluster Timing**

Media exchange and timing between clusters, including maintaining asynchronous operation across WAN-connected sites, remain subjects for further study.

### **Status & metrics logging**

Documentation of modifications made through the ingress conformance process against the resulting Flow timeline. Include mechanisms to support error detection and handling, as well as traceability of original OTS from conformed Flows.

### **Timing planes for alignment**

Definitions of Signal alignment principles 

[image1]: <data:image/png;base64,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>
