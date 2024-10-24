---
type: MT youtube-video
alias: let’s talk about apple intelligence…
---
 
[[MT youtube-video]]
[[BI Apple]]
[[IT artificial intelligence]]
[[IT online privacy]] 

<iframe width="560" height="315" src="https://www.youtube.com/embed/DLzOQYY6wjM?si=LvNgO2erP9y01VBc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

[[IT Trusted Execution Environment]] = A Trusted Execution Environment (TEE) is **a segregated area of memory and CPU that is protected from the rest of the CPU using encryption**

[[IT realm computing]] =  a reference security architecture and open-source implementation of hypervisor-based confidential computing, it is essentially a whole apart world of computing that is seperated from the typical hypervisor setup, all the memory used is encrypted even when idle, when there is a realm application running, nothing of it known to the typical normal hypervisor running on the same device

![[Pasted image 20240910164002.png]]

Attestation is the system by which something produces evidence about itself that another party can use to evaluate the trustworthiness of that entity -> [link](https://crypto.orange-labs.fr/acg/workshop/pdf/3-Attestation_in_ARM.pdf) 
used example: firmware attestation
for example when there is an application that needs compute, before it can be run, there will be a check to proof that the application is who it says it is

[3:31](https://www.youtube.com/watch?v=DLzOQYY6wjM&t=211) Private cloud compute is Apple’s solution to keep the AI models for Apple Intelligence private

[3:40](https://www.youtube.com/watch?v=DLzOQYY6wjM&t=220) ARM CCA hardware architecture

[5:07](https://www.youtube.com/watch?v=DLzOQYY6wjM&t=307) the current architecture of virtualisation cannot work with the private cloud setup needed for private AI computing

[5:31](https://www.youtube.com/watch?v=DLzOQYY6wjM&t=331) ARM trusted execution, code that runs in a secure part of the “word”/device

[6:00](https://www.youtube.com/watch?v=DLzOQYY6wjM&t=360) Trusted Execution Environment (TEE)

[6:19](https://www.youtube.com/watch?v=DLzOQYY6wjM&t=379) ARM realm extensions

[7:15](https://www.youtube.com/watch?v=DLzOQYY6wjM&t=435) this architecture makes it possible to run an application or service to run the LLM without it being accessible to the other parts of the CPU on that device. so this is how Apple can keep its Apple Intelligence private

[8:28](https://www.youtube.com/watch?v=DLzOQYY6wjM&t=508) firmware attestation

[9:19](https://www.youtube.com/watch?v=DLzOQYY6wjM&t=559) this model is the future of cloud compute

[9:52](https://www.youtube.com/watch?v=DLzOQYY6wjM&t=592) private clouds can work with this technology for example that what you use the cloud computing for is only readable by the realm you are using on the CPU and not by anyone else