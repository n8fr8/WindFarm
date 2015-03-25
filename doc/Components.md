#COMPONENTS

##CHIME

![a chime](http://media.giphy.com/media/aVG74zntJGZEY/giphy.gif)

Chime is the first defined behavior of Wind. It serves as the basic building block of communication, much like the hyperlink does on the Web. An application can broadcast a chime to indicate it is available to speak a specified protocol or offer a piece of content, using a specified radio technology at a specific address. It may also include authentication identifiers (public keys) and additional useful metadata to help consumers of the service decide whether they want to connect or not. Chiming is lightweight, lossy, transient and disposable. It is one-way and asynchronous, and both broadcasting and listening for chimes is meant to have little impact on battery or network scalability.

##LEAF

![a leaf](http://media.giphy.com/media/1AUG0F59WKMuI/giphy.gif)

A Leaf represents a unique piece of content on Wind that can be advertised via URI through a Chime, or discovered and distributed through any available protocol. A leaf differs from a page in that the replication, repeating or mirroring of the content, is inherently expected by the viewer of content. It is meant to be blown by the wind from the tree on which it is grown, and moved far beyond the original reach in whatever direction it is taken. Accessing a leaf is quite similar to accessing an HTTP link, and can even be done using the HTTP protocol over a Bluetooth socket connection, for instance. When a leaf is redistributed, metadata about the original source should always be included, and the content should be signed and verifiable through public key infrastructure, such that a known trusted source or authority can be verified. The source can also optionally include information related to expiration, license, and other helpful headers to encourage and manage its life cycle. There is no session or state when accessing a leaf. It is a single, disconnected event.

##TUNNEL

![tunnel car](http://media.giphy.com/media/11h0UVAzvaipI4/giphy.gif) ![tunnel plane](http://media.giphy.com/media/gtO9o3PvG95WE/giphy.gif)

A Tunnel is a direct connection between two or more devices for a real-time, interactive exchange of information. It may be in a client-server configuration using an HTTP like model, or it may be in a peer-to-peer model, as an exchange of state and messages. Tunnels are likely implemented as socket connections, usually in a Bluetooth Classic or WifiDirect IP context. The Tunnel is the path for complex custom protocols for one-to-one (private message)/and many-to-many (public status) to be implemented. Applications like file sharing and synchronization, secure messaging, and Twitter-status posting would all be implemented within Tunnel. However, awareness of these services being available or content queued for access is done through Chimes and Leaflets. The goal is to increase scalability and reduce wasted battery and processor time by only tunneling when absolutely necessary.
