# IPL Winner Prediction

- [IPL Winner Prediction](#ipl-winner-prediction)
	- [Installation](#installation)
	- [`streamlit` deployment to `heroku`](#streamlit-deployment-to-heroku)
		- [Create `Procfile`](#create-procfile)
		- [Create `setup.sh` to run `sreamlit`](#create-setupsh-to-run-sreamlit)
		- [Deploy to `heroku`](#deploy-to-heroku)

## Installation

> make sure training/testing and production have the same version of libraries

Getting versions:


```python
import sklearn
sklearn.__version__
# 1.0.2
```

Install Required dependencies:


```bash
pipenv install scikit-learn==1.0.2 pandas
```

## `streamlit` deployment to `heroku`

### Create `Procfile`

```procfile
web: sh setup.sh && streamlit run app.py
```

### Create `setup.sh` to run `sreamlit`

```sh
mkdir -p ~/.streamlit/

echo "\
[server]\n\
port = $PORT\n\
enableCORS = false\n\
headless = true\n\
\n\
" > ~/.streamlit/config.toml
```

### Deploy to `heroku`

```sh
heroku login
heroku create ipl-ai-project
git add -A
git commit -m "push to heroku"
git push heroku main
```