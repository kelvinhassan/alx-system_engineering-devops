<h1>0x19. Postmortem</h1>
<h3>Issue Summary</h3>
<p>from 0800 hours to 1200 hours, request to the student’s portal hosted in our server room resulted in error 500 as services were not available, this resulted to various complains from the student’s population as they were required to process exam cards. The root cause to this error was due to an invalid update to the portals db packages which had corrupted the students’ records.</p>
<h3>Timeline (+3 GMT)</h3>
<ul>
<li>0800 HRS: database update begins</li>
<li>0830 HRS: Outage begins</li>
<li>0900 HRS: Pagers alerted teams</li>
<li>0945 HRS: Failed configuration change rollback</li>
<li>1050 HRS: Successful configuration change rollback</li>
<li>1130 HRS: Server restarts begin</li>
<li>1200-HRS: 100% of traffic back online</li>
</ul>
<h3>Root Cause</h3>
<p>At around 0700 hours the server downloaded updates to most software’s installed as an auto update had been set on most applications, this resulted to the database upgrading which changed the schema on how the data for some of the web applications was done and request to access pages querying from these databases resulted in an error, this was because of a bug that was downloaded with update that resulted in so many changes to tables in the db, this caused the server to permanently block the db and all requests would end up with an error 500, the server began to restart repeatedly in attempt to restore the database configuration and outage began at 0830 hours</p>
<h3>Resolution and Recovery</h3>
<p>At 0900 hours the monitoring system alerted our engineers who quickly investigated the cause to the downtime, the issue was escalated to the top management and as the response team we began preparing the recovery procedures.</p>
<p>At 0900 hours the monitoring system alerted our engineers who quickly investigated the cause to the downtime, the issue was escalated to the top management and as the response team we began preparing the recovery procedures.</p>
<p>At 1050 hours the database restoration completed and we decided to restart the server so that all services would be started a fresh and services would be restored to a 100% at 1200 hours.</p>
<h3>Corrective and preventive measures</h3>
<p>In the last five days we conducted a review and analysis of the outage, the following are actions we are taking to address the underlying causes of the issue to help prevent further occurrence and improve response time.</p>

<ul>
<li>Disable automatic updates to applications on the production server and test updates before allowing them on production servers</li>
<li>Change rollback process to be quicker</li>
<li>Fix the current page load requirements to query from the database on load</li>
<li>Programmatically enforce stage rollouts of all configuration changes</li>
</ul>
<p>Kist is committed to continually and quickly serve its customers with ease and to use the available technologies to make services available and accessible to all for faster and personalized services We appreciate your patience and again apologize for the impact to you, your users, and your organization. We thank you for your business and continued support.</p>

'''
Sincerely

Kelvin Kist IT Response
'''
