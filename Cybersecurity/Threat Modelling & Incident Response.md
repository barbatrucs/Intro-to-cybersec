Threat modelling is the process of reviewing, improving, and testing the security protocols in place in an organisation's information technology infrastructure and services.

A critical stage of the threat modelling process is identifying likely threats that an application or system may face, the vulnerabilities a system or application may be vulnerable to.
  
The threat modelling process is very similar to a risk assessment made in workplaces for employees and customers. The principles all return to:
- Preparation
- Identification
- Mitigations
- Review

  ![[threat modelling process.png]]

It is, however, a complex process that needs constant review and discussion with a dedicated team. 
An effective threat model includes:
- Threat intelligence
- Asset identification
- Mitigation capabilities
- Risk assessment
  
To help with this, there are frameworks such as 
- **STRIDE** (**S**poofing identity, **T**ampering with data, **R**epudiation threats, **I**nformation disclosure, **D**enial of Service and **E**levation of privileges) 
  [[Stride]]
- **PASTA** (**P**rocess for **A**ttack **S**imulation and **T**hreat **A**nalysis). 

A breach of security is known as an incident. And despite all rigorous threat models and secure system designs, incidents do happen. Actions taken to resolve and remediate the threat are known as Incident Response (IR) and are a whole career path in cybersecurity.

Incidents are classified using a rating of urgency and impact. Urgency will be determined by the type of attack faced, where the impact will be determined by the affected system and what impact that has on business operations.

![[urgency impact matrix.png]]
  
An incident is responded to by a **C**omputer **S**ecurity **I**ncident **R**esponse **T**eam (**CSIRT**) which is prearranged group of employees with technical knowledge about the systems and/or current incident. To successfully solve an incident, these steps are often referred to as the six phases of Incident Response that takes place, listed in the table below:

|                 |                                                                                                                                             |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| **Action**      | **Description**                                                                                                                             |
| Preparation     | Do we have the resources and plans in place to deal with the security incident?                                                             |
| Identification  | Has the threat and the threat actor been correctly identified in order for us to respond to?                                                |
| Containment     | Can the threat/security incident be contained to prevent other systems or users from being impacted?                                        |
| Eradication     | Remove the active threat.                                                                                                                   |
| Recovery        | Perform a full review of the impacted systems to return to business as usual operations.                                                    |
| Lessons Learned | What can be learnt from the incident? I.e. if it was due to a phishing email, employees should be trained better to detect phishing emails. |