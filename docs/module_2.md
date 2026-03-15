### Cloud and Virtualization

## Cloud and Cloud Services
# Types of Clouds
    There are four primary cloud models:

        Public clouds
            Cloud-based applications and services offered in a public cloud are made available to the general population. Services may be free or are offered on a pay-per-use model, such as paying for online storage. The public cloud uses the internet to provide services.

        Private clouds
            Cloud-based applications and services offered in a private cloud are intended for a specific organization or entity, such as the government. A private cloud can be set up using the private network of an organization, though this can be expensive to build and maintain. A private cloud can also be managed by an outside organization with strict access security.

        Hybrid clouds
            A hybrid cloud is made up of two or more clouds (example: part private, part public), where each part remains a separate subject, but both are connected using a single architecture. Individuals on a hybrid cloud would be able to have degrees of access to various services based on user access rights.

        Community clouds
            A community cloud is created for exclusive use by a specific community. The differences between public clouds and community clouds are the functional needs that have been customized for the community. For example, healthcare organizations must remian compliant with policies and laws (e.g., HIPAA) that require special authentication and confidentiality.

# Cloud Computing and Virtualization
    Dedicated Servers
    The terms "cloud computing" and "virtualization" are often used interchangeable; however, they mean different things. Virtualization is the foundation of cloud computing. Without it, cloud computing, as it is most-widely implemented, would not be possible.
    Over a decade ago, VMware developed a virtualizing technology that enabled a host OS to support one or more client OSs. Most virtualization technologies are now based on this technology. The transformation of dedicated servers to virtualized servers has been embraced and is rapidly being implemented in data center and enterprise networks.
    Virtualization means creating a virtual rather than physical version of something, such as a computer. An example would be running a "Linux computer" in your Windows PC.
    To fully appreciate virtualization, it is necessary to understand some of the history of server technology. Historically, enterprise servers consisted of a server OS, such as Windows Server or Linux Server, installed on a specific hardware. All server RAM, processing power, and hard drive space were dedicated to the service provided (e.g., web, email services, etc).
    The major problem with this configuration is that when a component fails, the service that is provided by this server becomes unavailable. This is known as a single point of failure. Another problem was that dedicated servers were underused. Dedicate servers often sat idle for long periods of time, waiting until there was a need to deliver the specific service they provide. These servers wasted energy and took up more space than was warranted by the amount of service provided. This is known as server sprawl.

# Virtualization
    Advantages of virtualization
        One major advantage of virtualization is overall reduced cost:

            Less equipment is required
                Virtualization enables server consolidation, which requires fewer physical devices and lowers maintenance costs.
            Less energy consumed
                Consolidating servers lowers the monthly power and cooling costs
            Less space is required
                Server consolidation reduces the amount of required floor space

        These are additional benefits of virtualization:

            Easier prototyping
                Self-contained labs, operating on isolated networks, can be rapidly created for testing and prototyping network deployments
            Faster server provisioning
                Creating a virtual server is far faster than provisioning a physical server
            Increased server uptime
                Most server virtualization platforms now offer advanced redundant fault tolerance features
            Improved disaster recovery
                Most enterprise server virtualization platforms have software that can help test and automate failover before a disaster happens
            Legacy support
                Virtualization can extend the life of OSs and applications providing more time for organizations to migrate to newer solutions

# Hypervisors
    They hypervisors is a program, firmware, or hardware that adds an abstraction layer on top of the physical hardware. The abstraction layer is used to create virtual machines which have access to all the hardware of the physical machines such as CPUs, memory, disk controller, and NICs. Each of these virtual machines runs a complete and separate operatinf system. With virtualization, it is not uncommon for 100 physical servers to be consolidated as virtual machines on top of 10 physical servers that are using hypervisors.
    
