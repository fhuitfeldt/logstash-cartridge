logstash-cartridge
==================

This cartridge is customized to facilitate analysis of DCO logfiles.

To get started: 

copy in some test data (called server.log into logstash-1.4.0/logs) 
fix logstash conf to refer correctly to the newly created logfile (for some reason logstash does not accept relative paths for files)

cd logstash-1.4.0
./bin/logstash -f logstash.conf

This will get a basic logstash session running and it will parse your server.log to stdout

Next step

cd elasticsearch-1.1.0
./bin/elasticsearch

this will start elasticsearch on localhost

comment in the elastic search line in the output area of the logstash.conf

restart logstash.

this should populate elasticsearch with data from the parsed logfile.
the contents can be checked through the URL http://localhost:9200

Next step

to view the elasticsearch data in kibana:
cd kibana
open index.html
press src
Setting a global default dashboard
press "here" under "Setting a global default dashboard" in the left hand column

*adjust the date filter accoding to the timeslice that the logfiles represent*

This should show a basic overview of the events that were parsed.

....


to access jobtimings dashboard, open index.html#/dashboard/file/jobtimings.json (for example file:///Users/fmadsen/branches/logstash-cartridge/kibana/src/index.html#/dashboard/file/jobtimings.json)
It ain't much, but currently this is what we have