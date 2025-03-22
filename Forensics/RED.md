# RED

This challenge requires us to extract the flag from an image of just a red block. The flag is hidden in the metadata of the picture. I ran this through a couple of metadata extractor tools like `exiftools` and `zsteg` and `zsteg` found some hidden metadata in the file that looks to be base64 encoded. Running that data through a base64 decryptor and we get the flag.
