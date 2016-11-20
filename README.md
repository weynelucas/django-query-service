# django-query-service
Service to perform generic queries on models based on request params
## Methods
* `perform_query`: Performs a query in a model given the request parameters
* `perform_lookup_query`: Perform a query in a model to lookup the occurrence of the given argument in all model fields
* `paginate_list`: Paginate a list of objects

## Example
```python
from .models import Post
from django.shortcuts import render
from query_service import perform_lookup_query, paginate_list

def index(request):
  params =  request.GET
  objects = perform_lookup_query(model = Post, params = params)
  pagged_objects = paginate_list(objects, params)
  
  context = {
    'post_list': pagged_objects,
  }
  
  return render(request, 'index.html', context)
```
