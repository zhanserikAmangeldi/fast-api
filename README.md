# My way of Learning FastAPI

There you can see all my way of learning FastAPI

## First day 30/11/2024

Got understanding of how in base work FastAPI using official documentations[https://fastapi.tiangolo.com/].

### Creating endpoints

Easy to create, simple structure, with decorator. For example:

```python
from fastapi import FastAPI()

app = FastAPI()

@app.get("/")               # method("endpoint")  
def read_root():
    return {"Hello": "World"}
```

### Creating models

We can use anything how i understand, but official documentation recommend `pydantic`. For example:

```python
from pydantic import BaseModel

class Item(BaseModel):      
    name: str               
    price: float
    is_offer: Union[bool, None] = None
```

**NOTE**: `Union` is module from `typing` library, and is mean that for example from code above, that is_offer can be `bool` or `None`, assign is default value.

### Creating endpoint with path parameters and query parameters

```python
@app.get("/items/{item_id}")               # method("endpoint")  
def read_item(item_id: int, q: Union[str, None] = None):
    return {"item_id": item_id, "q": q}
```

### Intro to CRUD, put

Like with query parameters, add needed to get objects in argument.

```python
@app.put("/items/{item_id}")
def update_item(item_id: int, item: Item):
    return {"item_name": item.name, "item_id": item_id}
```

### How to run

```bash
fastapi dev main.py
```
