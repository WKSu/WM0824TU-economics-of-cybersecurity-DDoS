
# of DRDoS Honeypots:   7   (from sensor001 to sensor007)
# of Services:          6   (except sensor002)

List of Services:
    QOTD    17/udp
    CHG     19/udp
    DNS     53/udp
    NTP     123/udp
    SNMP    161/udp
    SSDP    1900/udp

Filenames:
    <sensor-id>_<service>_<date>_attack.csv

    sensor-id   Sensor's ID (from sensor001 to sensor007)
    service     Service name (see "List of Services")
    date        Date (timezone: JST, UTC+09:00)

Attack Definition:
    The sequence of packets that includes at least 100 consecutive requests
    to our honeypots. "consecutive" means that there was no gap of 60
    seconds or more between two packets. 

CSV Column:
    sensor-id,service,target-ip,country,as,hostname,start-time,stop-time,
    duration,packets,ip-id-list,ip-ttl-list,udp-sport-list

    In DNS cases, the 3 columns follows.
    dns-id-list,dns-qname-list,dns-qtype-list

    sensor-id       Sensor's ID (from sensor001 to sensor007)
    service         Service name (see List of Services)
    target-ip       IP address of the attack target.
    country         Country of the target-ip (by GeoIP Lite database).
    as              AS info of the target-ip (by GeoIP Lite database).
    hostname        Reverse lookup of the target-ip.
    start-time      Start time of the attack (JST).
    stop-time       Stop time of the attack (JST).
    duration        Duration of the attack (second).
    packets         The number of the attack packets.
    ip-id-list      List of ID field values in IP header.
    ip-ttl-list     List of TTL field values in IP header.
    udp-sport-list  List of source port fields in UDP header.
    dns-id-list     List of ID field values in DNS header.
    dns-qname-list  List of FQDNs used for DNS reflection attack.
    dns-qtype-list  List of query types used for DNS reflection attack.

    NOTE:
        If the length of *-list column is over 100, the column is shrunk and
        ends with '...'.
