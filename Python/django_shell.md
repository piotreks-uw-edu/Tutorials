### Open the Django shell
python manage.py shell

### Exit the shell
exit()

### delete all rows from a table: inside the Django shell
from quiz.models import Tag
Tag.objects.all().delete()