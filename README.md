# django-pagination
This is the pagination created in Django.


Inside your app, create a context_processor.py file.

```
from .models import <your_model Class>
from django.core.paginator import Paginator

def <your function>:
  # PAGINATOR code from here
  # ('-date') reversed your date and list from latest date where 'date' is your model fild name.
  `news_pagination = <your_model Class>.objects.all().order_by('-date')`
  
  # we pass 8 number because we want only 8 number of post per page.
  paginator = Paginator(news_pagination, 8)
  # page is the urls name. for example 'localhost:8000/news?page=2'.
  page_num = request.GET.get('page')
  imagecontext = paginator.get_page(page_num)
  
  context = {
    'imagecontext': imagecontext, 
  }
  
  return (context)

```
