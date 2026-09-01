# OPC UA Bulk Writer

This utility connects from any machine that can reach the Linux VM TCP endpoint and sends one OPC UA WriteRequest containing every row in `nodes.csv`.

## Requirements
- Java 17+
- Maven 3.8+
- Prosys endpoint with SecurityPolicy=None and Anonymous access enabled
- VM firewall/security group allows the OPC UA TCP port

## Build
```bash
mvn clean package
```

## Run
```bash
java -jar ".\target\opcua-bulk-writer-1.0.0.jar" "opc.tcp://10.16.14.56:53530/OPCUA/SimulationServer" "ns=3;i=1008" "90"
```

Replace the endpoint with the exact URL shown in Prosys **Endpoints** tab. Replace sample node IDs and types in `nodes.csv`.

CSV format:
```csv
nodeId,type,value
ns=3;i=1001,double,12.5
ns=3;s=Enable Bit,boolean,true
```

Supported types: boolean, int16, int32, int64, uint16, uint32, uint64, float, double, string.
