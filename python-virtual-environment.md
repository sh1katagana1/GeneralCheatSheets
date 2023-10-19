# Python Virtual Environment 
There is a lot of time you may be doing a pip install of a tool but it errors out due to a mismatch in other package versions needed for the tool. For this problem you can create a virtual environment in Python to have kind of a self contained space to install and run the tool. \
First we create our virtual environment using the venv tool
```
python3 -m venv venv
```
Then we activate it
```
source venv/bin/activate
```
This should now show you in a venv directory where you can proceed to install things via pip. When your done with it, you do:
```
deactivate
```
If you want to get back into a previously created environment
```
source venv/bin/activate
```
