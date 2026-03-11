from flask import Flask, request, send_file

from client.uploader import upload_blob
from client.downloader import download_blob

import os

app = Flask(__name__)


@app.route("/upload", methods=["POST"])
def upload():

    file = request.files["file"]

    path = f"/tmp/{file.filename}"

    file.save(path)

    blob_id = upload_blob(path)

    return {"blob_id": blob_id}


@app.route("/download/<blob_id>")
def download(blob_id):

    output = f"/tmp/{blob_id}"

    download_blob(blob_id, output)

    return send_file(output)


def start():

    app.run(host="0.0.0.0", port=8000)
