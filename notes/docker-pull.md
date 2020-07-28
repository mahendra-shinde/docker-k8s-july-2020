# docker pull <IMAGE>

1. Check AUTHORIZATION (public/private: requires right creds)
2. Download the IMAGE manifest (JSON)
    If no manifest found(400/500), pull failed!
3. Compare Manifest with Current docker-deamon for compatibility
    If not compatible, throw an error and stop
4. Check the IMAGE LAYERS inside image, and verify how many layer are available locally
5. Skip the available layers, and download only un-available one's.

Hosted Container Registries:
      ACR from Azure, ECR from Amazon, GCR from Google

Best Practice:
	No USER would be given PUSH access to registry!
 	Force use of CI Pipeline for PUSH operations