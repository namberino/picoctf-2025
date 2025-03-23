# Ph4nt0m 1ntrud3r

This requires us to analyze a pcap file. I loaded it into wireshark and checked out the TCP packets. Some of the TCP packets contain a base64 encoded string. After running it through a base64 decoder and rearranging it around a little bit, we get the full flag.
