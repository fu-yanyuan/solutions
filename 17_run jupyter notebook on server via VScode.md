Run .ipynb on server
---  

### need to install extensions on VS Code
  1. ssh to the remote server via vscode
  2. click the `Extensions` (ctrl+shift+X)  
     - you can see `LOCAL - INSTALLED` and `SSH: SERVER_NAME - INSTALLED` 
     - make sure that python extension and jupyter extension are installed in `SSH: SERVER_NAME - INSTALLED`  
       (extensions intalled locally are not automatically installed on remote server)
  3. open a .ipynb file or create a new one.
     - open command palette `view->command palatte` or ctrl+shift+P
     - create a new jupyter notebook: `>Jupyter: Create New Blank Notebook`
     - or just open a .ipynb file
  4. Select python interpreter of the notebook
     - open command palette `view->command palatte` or ctrl+shift+P
     - `>Python: Select Interpreter`
     - choose a conda env
     - if missing some modules, open the terminal and just use conda to install it.
     - ipykernel package. `conda install -n gans ipykernel --update-deps --force-reinstall`
  5. run the code
