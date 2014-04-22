alert driven infrastructure with nagios
=======================================

##Alert Driven Development

###IDEA
In software development we do ATDD (or outside-in development) to create application, can we do something similar with infrastructure?
There's already something similar with things like chefspec and serverspec testing frameworks, but they feel more like frameworks
for unit and intergration testing.  What's similar to acceptance criteria in the operations world?  Alerts!  We want to define our system 
by specifying what's really important to us - monitoring and alerting around the things we'll use for capactiy planning etc.

###HOW
 
- Use Nagios to define some alerts on a system that doesn't exist
- Set the thresholds down to 0 (so that alerts will fire as soon as the infrastructure is there)
- TDI the infrastructure with chef, chefspec & serverspec
- One it's up, the alerts should be firing (NOTE: alerts will be firing the whole time but for different reasons, once infrastructure is
        there they should be firing because the threshold has been breached)
- Add some load to the infrastructure and monitor the things you're going to alert on
- Set the thresholds to meaningfull values (See Art of Capacity Planning - required amount + ~20% headroom)
- Watch alerts go green!

###IMPORTANT BITS
We're describing the system in terms of the things we think are important.  Like, is the system up?  
 - alert on a heartbeat failure

Is the system working correctly?
 - if this is a webserver, is it serving web content?  Is the web server responding?

Does the system have ample capacity?
- alert on cpu higher than X%
- alert on memory higher than XGb

###TAKING THINGS FURTHER
Describe the distributed system in terms of alerts; what constitutes an outage?  Systems x,y and z need to be out?
Or perhaps x% of Y systems need to be out and z% of Q systems need to be out?  Alert on your alerts!  Can you do this
with nagios?

