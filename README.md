# Module-ietf-interfaces2
Module ietf-interfaces2

Easy implementation of module ietf-interfaces, in order to understand list mechanisms in OpenYuma

Steps:
install OpenYuma or yuma123...
put ietf-interfaces2.yang  in /usr/share/yuma/modules/netconfcentral/
do make_sil_dir ietf-interfaces2 in /usr/src/OpenYuma/exmaple-modules
in the ../src directory replace the default ietf-interfaces2.c by ietf-interfaces2.c in this repository.
do : 
make
make install
then launch server : /usr/sbin/netconfd --module=ietf-interfaces2 --factory-startup

the result:
yangcli admin@localhost> xget /interfaces-state2

RPC Data Reply 7 for session 1:

rpc-reply {
  data {
    interfaces-state2 {
      interface eth0 {
        name eth0
        statistics {
          in-octets 1296
          in-unicast-pkts 16
          in-errors 0
          in-discards 0
          in-multicast-pkts 0
          out-octets 738
          out-unicast-pkts 9
          out-errors 0
          out-discards 0
        }
      }
      interface lo {
        name lo
        statistics {
          in-octets 602965
          in-unicast-pkts 2413
          in-errors 0
          in-discards 0
          in-multicast-pkts 0
          out-octets 602965
          out-unicast-pkts 2413
          out-errors 0
          out-discards 0
        }
      }
    }
  }
}

you can make sure:
root@f582b13d4b55:/usr/src/OpenYuma# ifconfig
eth0      Link encap:Ethernet  HWaddr 02:42:ac:11:00:01  
          inet addr:172.17.0.1  Bcast:0.0.0.0  Mask:255.255.0.0
          inet6 addr: fe80::42:acff:fe11:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1296 (1.2 KB)  TX bytes:738 (738.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2412 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2412 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:602621 (602.6 KB)  TX bytes:602621 (602.6 KB)
