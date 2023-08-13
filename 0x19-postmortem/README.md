POSTMORTEM: WEB STACK OUTAGE INCIDENT 

Written by
Dominic Donatus Udousoro
dominicudosuoro@gmail.com

Issue Summary:

Duration: April 15, 2023, 10:30 - April 15, 2023, 13:45 (UTC)

Impact: Web Application Service Downtime

Affected Service: User Dashboard

User Impact: Approximately 41% of users experienced complete unavailability of the User Dashboard. Remaining users experienced severe performance degradation and slow loading times, affecting their ability to use the application effectively.


Timeline:

	10:30: The issue was detected as a flurry of customer complaints regarding the inaccessible User Dashboard flooded customer support.

	10:35: An alert received from the monitoring system indicated a sudden surge in error rates, prompting the engineering team's attention.

	10:40: The initial investigation commenced, focusing on analyzing database performance metrics and server health indicators.

	11:00: The assumption was made that the root cause lay in a potential database overload due to an unusually high number of connections.

	11:30: Resources and tools were allocated to the database cluster to handle the assumed spike in traffic. However, this yielded no expected results, instead the issue persisted.

	12:00: The scope of investigation expanded to encompass the load balancer configuration, given the persistent problem.

	12:30: Verification of the load balancer settings were meticulously carried out; unfortunately, no immediate improvement was observed. This was followed by security checks for possible breaches which proved that the issue had nothing to do with security attacks.

	13:00: Recognizing the complexity and intricacy of the issue, the incident was escalated to senior database administrators and network specialists for further holistic examination.

	13:15: The senior team immediately identified a network misconfiguration that led to internal requests loop back, which created a loop of redundant and superfluous requests that clustered and overwhelmed the database.

	13:45: The incident was finally resolved by reconfiguration of the network to prevent the looping of internal requests. Affected services were restarted and returned to normalcy.

Root Cause and Resolution:
	Root Cause: The root cause of the outage was determined to be a network misconfiguration leading to the creation of a feedback loop for internal requests. This loop resulted in an excessive number of redundant requests overwhelming the database, causing severe performance degradation and unavailability of services.

	Resolution: To address the issue, the engineering team reconfigured the network settings to halt the looping of internal requests. Additionally, a thorough cleanup of the backlog of redundant requests was executed. Affected services were restarted to establish a clean state and restore optimal functionality.

Corrective and Preventative Measures:
Improvements/Fixes:
1. Enhanced Network Monitoring: Implement more robust and comprehensive network monitoring to detect abnormal patterns and misconfigurations in real-time.
2. Automated Testing: Develop automated tests that simulate abnormal request patterns and potential loopholes in the network configuration, ensuring early identification of vulnerabilities.
3. Strengthened Communication Channels: Foster clearer and more direct communication channels between development and operations teams, facilitating swifter incident identification, escalation, and resolution.

Tasks to Address the Issue:
1. Network Configuration Review: Conduct holistic network configuration review guidelines to identify potential vulnerabilities and eliminate misconfigurations.
2. Network Redundancy Implementation: Design and implement network redundancy mechanisms to minimize the impact of single points of failure.
3. Runbook Development: Create a comprehensive runbook explaining in details, the steps to identify and mitigate scenarios relating to database overload and network misconfigurations.
4. Incident Escalation Path: Establish a clear and well-defined incident escalation path to ensure the swift involvement of senior specialists when dealing with critical incidents.
5. Post-Incident Review: Regularly conduct post-incident review meetings to analyze the effectiveness of incident response strategies and pinpoint areas for improvements and further enhancement.

In conclusion, the web stack outage incident on April 15th, 2023, highlighted the critical importance of robust network configuration and monitoring. The incident resulted in a substantial service downtime, affecting both availability and performance. By identifying the root cause as a network misconfiguration, rectifying it, and implementing corrective and preventive measures, the organization has taken steps to fortify its systems against similar occurrence in the future.

