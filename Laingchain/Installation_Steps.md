# Installation steps :
## open cmd/bash of your current directory/folder :


## 1. Create a Virtual Environment :
### on windows:
```
python -m venv myenv
```
### on mac/ios:
```
python3 -m venv myenv
```

## 2. Activate the Virtual Environment :
### on windows:
```
myenv\Scripts\activate
```

### on mac/ios:
```
source myenv/bin/activate
```

## Deactivate When Done :
```
deactivate
```

## 3. Create a file called requirements.txt :
- langchain
- openai

## 4. Install these library/requirements.txt :
```
pip install -r requirements.txt
```

## 5. Create a file called langchain.ipynb for jupyter notebook.

## 6. Create a file called .env and put open ai key there :
```
OPENAI_API_KEY="your_api_key"
```