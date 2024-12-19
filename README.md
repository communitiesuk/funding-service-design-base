> [!IMPORTANT]
> This concept was superseded by reducing the number of apps and duplicated requirements. At the time of archiving these are https://github.com/communitiesuk/funding-service-pre-award-frontend and https://github.com/communitiesuk/funding-service-pre-award-stores

# funding-service-design-base
Base images and requirements definitions for development of funding service design apps. These images are not used in production as those ones are build using Paketo.

## Python Flask Dev
Contains requirements files for different versions of a python flask app. The [Dockerfile](./python-flask-dev/Dockerfile) contains the following build targets:
- `flask`: Developer image based on python 3.10 bullseye, with Flask 3.0.3 installed on top, plus everything in [requirements-dev.txt](./python-flask/requirements-dev.txt)
- `frontend`: Base on `flask` above, with everything from [requirements-frontend.txt](./python-flask-dev/requirements-frontend.txt) installed

## Workflows
- [Publish](/.github/workflows/publish.yml): Uses a matrix strategy to build each target in the Dockerfile and publish these to GHCR. If on `main`, will tag them as specified in [tags](./python-flask-dev/tags). (At present if you add something to tags you also need to add to [publish.yml](./.github/workflows/publish.yml)).

# Future Improvements
- Make the workflow just use all tags in the tags file, not hard code them?
- If we add other base images besides [python-flask](./python-flask/), make the workflow use a matrix approach so it builds all of these?
- Are we using the right tag names?
- Stop using pip-compile and use rye?
