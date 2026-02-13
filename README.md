# hTorrent - Torrent parser and Bencode serializer/deserializer library

hTorrent provides classes and methods for:

- Deserializing tracker responses
- Deserializing torrent files
- Serializing torrent files


## Classes

### Info

Represents the info dictionary. The raw bytes are perserved as it is needed for the infohash.

#### Properties 
- Length - long?
- Files - List<File>?
- Private - long?
- Source - byte[]?
- ExtraFields - Dictionary<byte[], object>?
- Name - byte[]
- PieceLength - long
- Pieces - byte[]?
- RawBencodedInfo - byte[]?
- Md5Sum - byte[]?
- Sha1 - byte[]?
- Sha256 - byte[]?
- NameString - string
- IsPrivate - bool
- SourceString - string
- PieceCount - int
- PieceHashes - IEnumerable<byte[]>


### File

Represents a single file. Path is a list of byte[] because each byte[] represents a subfolder of the file's path.

#### Properties 
- Length - long
- Path - List<byte[]>

### Torrent

Represents a single torrent. Torrents can be created either through the TorrentBuilder method or by calling the default constructor and initializing the property values.  

#### Properties 
- Announce - byte[]?
- AnnounceList - List<List<byte[]>>?
- ExtraFields - Dictionary<byte[], object>?
- Publisher - byte[]?
- PublisherUrl - byte[]?
- EncodingType - byte[]?
- Info - Info?
- Comment - byte[]?
- Ver - Version
- CreatedBy - byte[]?
- CreationDate - long?
- Sources - List<byte[]>?
- UrlList - List<byte[]>?
- CreationDateTimeOffset - DateTimeOffset?
- AnnounceString - string
- CommentString - string
- PublisherString - string
- PublisherUrlString - string
- EncodingTypeString - string
- CreatedByString - string
- AnnounceListStrings - IEnumerable<IEnumerable<string>>?


### Parser

Handles the majority of the parsing. Takes in a byte array then returns an AST, which is then passed to Map. 

### Serializer 

Handles serialization. Calls the Torrent class's ToBencodeModel method, then writes the bytes to the memory stream. 

## Methods 

### Torrent.TorrentBuilder

Takes in a filename as a string and returns a Torrent object. 

### Parser.DecodeBencodeObject

Parses a Bencode string to a CLR object. This technically can be used for parsing torrents but I intended it to be used to parse tracker responses.

### Serializer.SaveTorrentAsFile

Very straightforward, takes in a Torrent instance and a file path as parameters and writes the file to disk. 


## What is not currently supported

- V2 support
- Magnet link parsing/generation

## Installation 
```dotnet add package hTorrent --version 1.0.0```
