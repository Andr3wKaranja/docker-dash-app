# Docker Dash App
<!-- A simple design for a plotly-dash app with sklearn running within a docker container deployed to [Heroku]() using CI/CD. [![Continuous Integration and Delivery](https://github.com/ROpdam/docker-dash-example/actions/workflows/main.yml/badge.svg?branch=master)](https://github.com/ROpdam/docker-dash-example/actions/workflows/main.yml)  -->
 
Inspired by [This Medium article](https://towardsdatascience.com/deploy-containeriazed-plotly-dash-app-to-heroku-with-ci-cd-f82ca833375c)
 
### Using [pre-commit-hooks](https://pre-commit.com/)
- flake8 
- black
- isort

### Structure
```
├── .github
│   └── workflows
│        └── main.yml
│
├── project
│   ├── app
│   │   ├── __init__.py
│   │   ├── app.py
│   │   ├── functions.py
│   │   └── assets
│   ├── Dockerfile
│   ├── Dockerfile.prod
│   └── requirements.txt
│
├── release.sh
├── setup.cfg
├── .pre-commit-config.yaml
├── .gitignore
│
└── README.md
```
### Repo Break-Down
1. The `.github` folder contains a workflow `main.yml` file that is used in Github Actions for the CI/CD pipeline to deploy the app.
2. `Project` folder contains a folder with the Plotly Dash App, its assets (.css file in our case), the requirements.txt file containing the necessary packages, a Dockerfile for local deployment and a Dockerfile.prod for deployment on Heroku.
3. `release.sh` is used to release the app on Heroku.
4. `pre-commit-config.yaml` and `setup.cfg files` are used for code styling and linting



### Run locally
To run the image locally, cd into the docker-dash-example folder and:
```
docker build -t docker-dash project/.
```
And run the container
```
docker run -p 8050:8050 docker-dash
```
You can find to the app on your local machine http://0.0.0.0:8050/. This way the image is created using the Dockerfile, instead of the Dockerfile.prod.