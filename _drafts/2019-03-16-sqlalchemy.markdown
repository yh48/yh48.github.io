


```
sqlalchemy.exc.InvalidRequestError: One or more mappers failed to initialize - can't proceed with initialization of other mappers. Triggering mapper: 'Mapper|MyClass|my_property'. Original exception was: Error creating backref 'my_property' on relationship 'Myclass.my_property2': property of that name exists on mapper 'Mapper|MyClass2|my_property2'
```





```python
class WordCategory:
  word = relationship("Word", foreign_keys=[word_id], back_populates='word_category')

class Word:
  word_category = relationship("WordCategory", back_populates="word", uselist=False)
```
