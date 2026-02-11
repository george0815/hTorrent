# hTorrent - Torrent parser and Bencode serializer/deserializer library

hTorrent provides classes and methods for:

- Deserializing tracker responses
- Deserializing torrent files
- Serializing torrent files


## Classes

### Info

Represents the info dictionary. The raw bytes are perserved as it is needed for the infohash.


#### Properties 


### File

Represents a single file. Path is a list of byte[] because each byte[] represents a subfolder of the file's path.

#### Properties 
- Length - long
- Path - List<byte[]>

### Torrent

Represents a single torrent. Torrents can be created either through the TorrentBuilder method or by calling the default constructor and initializing the property values.  

#### Properties 



### Parser

Handles the majority of the parsing. Takes in a byte array then returns an AST, which is then passed to Map. 

#### Properties 


### Serializer 

Handles serialization. Calls the Torrent class's ToBencodeModel method, then writes the bytes to the memory stream. 

#### Properties 


## Methods 

### Torrent.TorrentBuilder

### Parser.DecodeBencodeObject

### Serializer.SaveTorrentAsFile


## What is not currently supported

- V2 support
- Magnet link parsing/generation 
