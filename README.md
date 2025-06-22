![Result_Task](https://github.com/user-attachments/assets/95d85092-274d-4134-a3dd-7517d5f5831b)

Ref:
Teaching Computer Networking with Mininet Te-Yuan Huang, Vimalkumar Jeyakumar Bob Lantz, Brian O'Connor Nick Feamster Keith Winstein, Anirudh Sivaraman


Code
#!/usr/bin/python

from mininet.topo import Topo
from mininet.net import Mininet
from mininet.node import Controller, RemoteController
from mininet.cli import CLI
from mininet.log import setLogLevel

class SimpleTopo(Topo):
    def build(self):
        # Add hosts
        h1 = self.addHost('h1', ip='10.0.0.1/24')
        h2 = self.addHost('h2', ip='10.0.0.2/24')

        # Add switch
        s1 = self.addSwitch('s1')

        # Add links
        self.addLink(h1, s1)
        self.addLink(h2, s1)

def run():
    topo = SimpleTopo()
    net = Mininet(topo=topo, controller=Controller)     
    net.start()

    print("test ping")
    net.pingAll()

    CLI(net)
    net.stop()

if __name__ == '__main__':
    setLogLevel('info')
    run()
