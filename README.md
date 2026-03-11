# Aurora Blob Storage

Prototype distributed blob storage system.

Features:

- Blob upload
- Erasure coding
- Multi storage nodes
- RPC server
- Blob reconstruction

Architecture

Client → RPC → Storage Nodes

Run server

python main.py

Upload

curl -F "file=@video.mp4" localhost:8000/upload

Download

localhost:8000/download/<blob_id>
