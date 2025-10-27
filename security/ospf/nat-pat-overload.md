NAT PAT overload:

enable
confi t
in gi0/0
ip nat inside
exit
in gi0/1
ip nat outside
exit
access-list 1 permit 10.0.0.0 0.255.255.255
ip nat inside source list 1 interface gi0/1 overload