### Python sort namedtuple

对于以下列表，试以分数进行递减排序
```python3
import collections
Student = collections.namedtuple('Student', ('name', 'score'))
Student_list = [Student(name="Simon", score=99), Student(name="天津风", score = 97), Student(name="Charlie", score=98), Student(name="il harper", score= -7)]
```

```python3
Sorted(Student_list, key=lambda x: x.score, reverse = True)
>>> [Student(name='Simon', score=99), Student(name='Charlie', score=98), Student(name='天津风', score=97), Student(name='il harper', score=-7)]
```
