This is a script that will migrate all of your metrics from graphite to influxdb. It will take some time but it just reads the data from graphite and then writes it to influx on the graphite input port. Prior to running this run bundle install and also set up the graphite section in the influxdb.conf file to accept on tcp port 2003 and to create the measurements properly in influx. 

EX 
[[graphite]]
bind-address = ":2003"
database = "graphite"
enabled = true
protocol = "tcp"
templates = ["*.cpu host.measurement.resource.field* ", "*.cpu.btime host.measurement.field* ", "*.cpu.ctxt host.measurement.field* ", "*.cpu.intr host.measurement.field* ", "*.cpu.processes host.measurement.field* ", "*.cpu.procs_blocked host.measurement.field* ", "*.cpu.procs_running host.measurement.field* ", "*.disk host.measurement.disk.field* ", "*.entropy host.measurement ", "*.events host.measurement.field* ", "*.interface host.measurement.interface.field* ", "*.loadavg host.measurement.field* ","*.load_avg host.measurement.field* ", "*.memory host.measurement.field* ", "*.ntpstats host.measurement.field* ", "*.peer_totals host.measurement.field* ", "*.peers host.measurement.resource.field* ", "*.proc host.measurement.resource.process.field* ", "*.rabbitmq host.measurement.resource.type.field* ", "*.redis host.measurement.field* ", "*.workers host.measurement.resource.field* ", "*.worker_totals host.measurement.field* ", "*.elasticsearch host.measurement.field* "]

Once influx is set up run the script like this. 
# $ ./worker.rb -g graphite.prod -i influx.prod -h 1y
