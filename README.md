# Jupyter-notebook-from-HPC
## Environment setting for openning jupyter notebook locally from HPC or other servers

## Environment: anaconda, jupyter notebook and installed on HPC

## Problem description
1. Cannot open Jupyter notebook on a browser from server.
2. Invalid credentials when trying to open the Jupyter notebook locally

## Solution
1. Generate a configure file
```
jupyter notebook --generate-config
Writing default config to: /lustre/home/acct-medkwf/medkwf4/.jupyter/jupyter_notebook_config.py
```
2. Open the config file, search for "NotebookApp.allow_password_change" and change it to NotebookApp.allow_password_change=False (**remove hashmark**)

3. Set password
> jupyter notebook password
> Enter password:
> Verify password:
> [NotebookPasswordApp] Wrote hashed password to /lustre/home/acct-medkwf/medkwf4/.jupyter/jupyter_notebook_config.json
A hashed password generated to the .json file

4. Find the hashed password and insert it to "c.NotebookApp.password" in jupyter_notebook_config.py, remove hashmark

5. Run jupyter notebook on server
> jupyter notebook --no-browser --port=8888 --ip=0.0.0.0
no-browser not open browser on the server
port can be any accessibale port

6. Set server port mapping to the local computer
Open cmd (win10):
> ssh username@server_ip -L127.0.0.1:8000:127.0.0.1:8888
map local port 8000 to the server port 8888, password is required

7. Open local browser and type http://127.0.0.1:8000, use the password set in step 3
![image](https://user-images.githubusercontent.com/72248852/158754331-ba8c9c01-514c-46de-ad8c-603978df80de.png)





