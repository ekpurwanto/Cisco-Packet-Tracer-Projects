## Network Overview

The VIC Modern Hotel network is designed using a hierarchical architecture:

- Access Layer: Switches per floor
- Distribution Layer: Router-on-a-Stick
- Routing: OSPF Area 0
- Segmentation: VLAN per department

Each floor operates independently but communicates via OSPF.
