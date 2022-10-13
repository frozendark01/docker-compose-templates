git clone https://github.com/kylemanna/docker-openvpn.git
cd docker-openvpn && docker build -t open-vpn-server .
mkdir vpn-data && touch vpn-data/vars
docker run -v $PWD/vpn-data:/etc/openvpn --rm open-vpn-server ovpn_genconfig -u udp://IP_ADDRESS:1194
docker run -v $PWD/vpn-data:/etc/openvpn --rm -it open-vpn-server ovpn_initpki
docker run -v $PWD/vpn-data:/etc/openvpn -d -p 1194:1194/udp --cap-add=NET_ADMIN open-vpn-server
docker run -v $PWD/vpn-data:/etc/openvpn --rm -it open-vpn-server easyrsa build-client-full user nopass
docker run -v $PWD/vpn-data:/etc/openvpn --rm open-vpn-server ovpn_getclient user > user.ovpn