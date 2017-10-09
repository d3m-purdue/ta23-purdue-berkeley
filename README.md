# ta23-purdue-berkeley
TA2/TA3 integration between Purdue and Berkeley teams

## Setup Instructions

1. Pull down the latest Berkeley TA2 Docker image: `docker pull
   registry.datadrivendiscovery.org/berkeley/aika`.

2. Clone the Modsquad TA3 repository: `git clone
   https://github.com/d3m-purdue/modsquad -b ta23-berkeley`.

3. Follow the build instructions at
   https://github.com/d3m-purdue/modsquad/README.md.

4. Download the seed dataset: `curl -O
   https://datadrivendiscovery.org/data/seed_datasets/r_22.tar.gz && gunzip
r_22.tar.gz`.  You may need to do this step through a web browser to handle D3M
credentials.

5. Copy the seed dataset into a shared directory for TA2 and TA3: `mkdir
   /storage/datasets/seed && cp -rv o_38 /storage/datasets/seed`.

6. Set global write permissions on the data directory: `sudo chmod -R go+w
   /storage/datasets`.

7. Launch the TA2 Docker container: `docker run --shm-size=1g -p 50001:50051 -v
   /storage:/data registry.datadrivendiscovery.org/berkeley/aika`.

8. Launch the TA3 server: `cd modsquad && PORT=8080
   JSON_CONFIG_PATH=./config.json npm run serve`.

9. Visit http://localhost:8080 to try out the integration.
