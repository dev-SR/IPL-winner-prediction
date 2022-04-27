# IPL Winner Prediction

- [IPL Winner Prediction](#ipl-winner-prediction)
	- [`streamlit` deployment to `heroku`](#streamlit-deployment-to-heroku)
		- [Create `Procfile`](#create-procfile)
		- [Create `setup.sh` to run `sreamlit`](#create-setupsh-to-run-sreamlit)
		- [Deploy to `heroku`](#deploy-to-heroku)

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