user@build-host:~$
git clone https://github.com/pravega/pravega-sensor-collector
cd pravega-sensor-collector
scripts/build-installer.sh

sudo mkdir -p /opt/pravega-sensor-collector
sudo tar -C /opt/pravega-sensor-collector --strip-components 1 \
   -xzvf /tmp/pravega-sensor-collector-*.tgz
   
cp /opt/pravega-sensor-collector/conf/env-sample-network-standalone.sh /opt/pravega-sensor-collector/conf/env-local.sh

sudo /opt/pravega-sensor-collector/bin/install-service.sh

sudo systemctl status pravega-sensor-collector.service
sudo journalctl -u pravega-sensor-collector.service



export PRAVEGA_CONTROLLER=tls://pravega-controller.sdp1.example.com:443
export PRAVEGA_SCOPE=edge
export PRAVEGA_STREAM=sensors
export CREATE_SCOPE=false
export pravega_client_auth_method=Bearer
export pravega_client_auth_loadDynamic=true
export KEYCLOAK_SERVICE_ACCOUNT_FILE=/opt/pravega-sensor-collector/conf/cancer.csv
export ROUTING_KEY=$(hostname)
export ENABLE_SENSOR_COLLECTOR=false
export ENABLE_PERSISTENT_QUEUE_TO_PRAVEGA=false
export SAMPLES_PER_EVENT=200
export LOG_FILE_INGEST_ENABLE=true
export LOG_FILE_INGEST_EVENT_TEMPLATE="{\"RemoteAddr\":\"$(hostname)\"}"
export LOG_FILE_INGEST_FILE_SPEC="/opt/dw/staging/*.csv"
export PRAVEGA_SENSOR_COLLECTOR_ACCEL1_CLASS=io.pravega.sensor.collector.file.LogFileIngestService
export PRAVEGA_SENSOR_COLLECTOR_ACCEL1_FILE_SPEC="/opt/dw/staging/*.csv"
export PRAVEGA_SENSOR_COLLECTOR_ACCEL1_DELETE_COMPLETED_FILES=true
export PRAVEGA_SENSOR_COLLECTOR_ACCEL1_DATABASE_FILE=/tmp/accelerometer.db
export PRAVEGA_SENSOR_COLLECTOR_ACCEL1_EVENT_TEMPLATE="{\"RemoteAddr\":\"$(hostname)\"}"
export PRAVEGA_SENSOR_COLLECTOR_ACCEL1_SAMPLES_PER_EVENT=200
export PRAVEGA_SENSOR_COLLECTOR_ACCEL1_PRAVEGA_CONTROLLER_URI=tls://pravega-controller.sdp.sdp-demo.org:443
export PRAVEGA_SENSOR_COLLECTOR_ACCEL1_SCOPE=edge
export PRAVEGA_SENSOR_COLLECTOR_ACCEL1_CREATE_SCOPE=false
export PRAVEGA_SENSOR_COLLECTOR_ACCEL1_STREAM=sensors
export PRAVEGA_SENSOR_COLLECTOR_ACCEL1_ROUTING_KEY=$(hostname)
export PRAVEGA_SENSOR_COLLECTOR_ACCEL1_TRANSACTION_TIMEOUT_MINUTES=2.0
export JAVA_OPTS="-Xmx512m"
